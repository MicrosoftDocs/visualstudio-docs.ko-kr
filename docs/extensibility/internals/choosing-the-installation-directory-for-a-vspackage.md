---
title: VSPackage 설치 디렉터리 선택 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ead19e9f50201ab795e3c3f68b661037d309d98d
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011907"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>VSPackage 설치 디렉터리 선택
VSPackage와 해당 지원 파일은 사용자의 파일 시스템에 있어야 합니다. 위치는 VSPackage 관리 되는지, 관리 되지 않는지, 병렬 버전 관리 체계 및 사용자 선택에 따라 달라 집니다.

## <a name="unmanaged-vspackages"></a>관리 되지 않는 Vspackage
 관리 되지 않는 VSPackage는 모든 위치에 설치할 수 있는 COM 서버입니다. 해당 등록 정보는 해당 위치를 정확 하 게 반영 해야 합니다. 설치 관리자 UI (사용자 인터페이스)는 기본 위치를 Windows Installer 속성 값의 하위 디렉터리로 제공 해야 합니다 `ProgramFilesFolder` . 예를 들면 다음과 같습니다.

*&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; MyVSPackageProduct &gt; \v1.0\\*

 사용자는 작은 부팅 파티션을 유지 하 고 다른 볼륨에 응용 프로그램 및 도구를 설치 하는 것을 선호 하는 사용자에 맞게 기본 디렉터리를 변경할 수 있어야 합니다.

 Side-by-side 스키마를 사용 하 여 버전이 지정 된 VSPackage를 사용 하는 경우 하위 디렉터리를 사용 하 여 다른 버전을 저장할 수 있습니다. 예를 들면 다음과 같습니다.

 *&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; MyVSPackageProduct v1.0 &gt; \\ \\ 2002\\*

 *&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; MyVSPackageProduct v1.0 &gt; \\ \\ 2003\\*

 *&lt;ProgramFilesFolder &gt; \\ &lt; MyCompany &gt; \\ &lt; MyVSPackageProduct v1.0 &gt; \\ \\ 2005\\*

## <a name="managed-vspackages"></a>관리되는 VSPackage
 모든 위치에 관리 되는 Vspackage을 설치할 수도 있습니다. 그러나 어셈블리 로드 시간을 줄이기 위해 항상 GAC (전역 어셈블리 캐시)에 설치 하는 것을 고려해 야 합니다. 관리 되는 Vspackage은 항상 강력한 이름의 어셈블리 이므로 GAC에 설치 하면 강력한 이름 서명 확인이 설치 시에만 수행 됩니다. 파일 시스템의 다른 위치에 설치 된 강력한 이름의 어셈블리에는 로드할 때마다 해당 서명이 확인 되어야 합니다. GAC에 관리 되는 Vspackage을 설치 하는 경우 regpkg 도구의 **/assembly** 스위치를 사용 하 여 어셈블리의 강력한 이름을 가리키는 레지스트리 항목을 작성 합니다.

 GAC 이외의 위치에 관리 되는 Vspackage을 설치 하는 경우 디렉터리 계층 구조를 선택 하기 위해 관리 되지 않는 Vspackage에 대해 지정 된 이전 조언을 따릅니다. Regpkg 도구의 **/codebase** 스위치를 사용 하 여 VSPackage 어셈블리의 경로를 가리키는 레지스트리 항목을 작성 합니다.

 자세한 내용은 [Vspackage 등록 및 등록 취소](../../extensibility/registering-and-unregistering-vspackages.md)를 참조 하세요.

## <a name="satellite-dlls"></a>위성 DLL
 규칙에 따라 특정 로캘에 대 한 리소스를 포함 하는 VSPackage 위성 Dll은 *VSPackage* 디렉터리의 하위 디렉터리에 있습니다. 하위 디렉터리는 LCID (로캘 ID) 값에 해당 합니다.

 [Vspackage 관리](../../extensibility/managing-vspackages.md) 문서는 레지스트리 항목이 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 실제로 VSPACKAGE의 위성 DLL을 찾는 위치를 제어 함을 나타냅니다. 그러나는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] LCID 값에 대해 라는 하위 디렉터리에 다음 순서로 위성 DLL을 로드 하려고 시도 합니다.

1. 기본 LCID (예: 영어의 경우 *\ 1033* )

2. 기본 하위 언어를 사용 하는 기본 LCID

3. 시스템 기본 LCID입니다.

4. 기본 하위 언어를 사용 하는 시스템 기본 LCID입니다.

5. 미국 영어 (*.\ 1033* 또는 *.\0x409*).

VSPackage DLL이 리소스를 포함 하 고 **SatelliteDll\DllName** 레지스트리 항목이이를 가리키는 경우는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 위의 순서로 로드 하려고 시도 합니다.

## <a name="see-also"></a>참고 항목
- [공유 및 버전 관리 Vspackage 중에서 선택](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [VSPackage 관리](../../extensibility/managing-vspackages.md)
- [패키지 등록 관리](/previous-versions/bb166783(v=vs.100))
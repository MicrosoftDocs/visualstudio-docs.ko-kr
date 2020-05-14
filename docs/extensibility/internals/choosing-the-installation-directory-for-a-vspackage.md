---
title: VS패키지에 대한 설치 디렉토리 선택 | 마이크로 소프트 문서
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
ms.openlocfilehash: b8391cbdd3a857ea4ebaf3a36655520935f1a128
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709756"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>VSPackage의 설치 디렉토리 선택
VSPackage 및 해당 지원 파일은 사용자의 파일 시스템에 있어야 합니다. 위치는 VSPackage가 관리되는지 관리되지 않는지, 나란히 버전 관리 방식 및 사용자 선택에 따라 달라집니다.

## <a name="unmanaged-vspackages"></a>관리되지 않는 VS패키지
 관리되지 않는 VSPackage는 모든 위치에 설치할 수 있는 COM 서버입니다. 등록 정보는 위치를 정확하게 반영해야 합니다. 설치 관리자 사용자 인터페이스(UI)는 `ProgramFilesFolder` Windows Installer 속성 값의 하위 디렉터리로 기본 위치를 제공해야 합니다. 다음은 그 예입니다.

*&lt;프로그램&gt;\\&lt;파일폴더&gt;\\&lt;마이컴퍼니 마이VS패키지제품&gt;\V1.0\\*

 사용자는 작은 부팅 파티션을 유지하고 다른 볼륨에 응용 프로그램 및 도구를 설치하는 것을 선호하는 사용자를 수용하도록 기본 디렉터리를 변경할 수 있어야 합니다.

 나란히 구성표가 버전이 지정된 VSPackage를 사용하는 경우 하위 디렉터리를 사용하여 다른 버전을 저장할 수 있습니다. 다음은 그 예입니다.

 *&lt;프로그램파일폴더&gt;\\&lt;마이컴퍼니&gt;\\&lt;마이VS패키지제품&gt;\\V1.0\\2002\\*

 *&lt;프로그램파일폴더&gt;\\&lt;마이컴퍼니&gt;\\&lt;마이VS패키지제품&gt;\\V1.0\\2003\\*

 *&lt;프로그램파일폴더&gt;\\&lt;마이컴퍼니&gt;\\&lt;마이VS패키지제품&gt;\\V1.0\\2005\\*

## <a name="managed-vspackages"></a>관리되는 VSPackage
 관리되는 VSPackage는 모든 위치에 설치할 수도 있습니다. 그러나 어셈블리 로드 시간을 줄이기 위해 항상 전역 어셈블리 캐시(GAC)에 설치하는 것이 좋습니다. 관리되는 VSPackage는 항상 강력한 이름의 어셈블리이므로 GAC에 설치하는 것은 강력한 이름 서명 확인이 설치 시에만 걸린다는 것을 의미합니다. 파일 시스템의 다른 위치에 설치된 강력한 이름의 어셈블리는 로드될 때마다 해당 서명이 확인되어야 합니다. GAC에 관리되는 VSPackage를 설치할 때 regpkg 도구의 **/어셈블리** 스위치를 사용하여 어셈블리의 강력한 이름을 가리키는 레지스트리 항목을 작성합니다.

 GAC 가 아닌 다른 위치에 관리되는 VSPackage를 설치하는 경우 디렉터리 계층 구조를 선택하기 위해 관리되지 않는 VSPackage에 대해 제공된 이전 조언을 따르십시오. regpkg 도구의 **/codebase** 스위치를 사용하여 VSPackage 어셈블리의 경로를 가리키는 레지스트리 항목을 작성합니다.

 자세한 내용은 [VSPackage 등록 및 등록 취소를](../../extensibility/registering-and-unregistering-vspackages.md)참조하십시오.

## <a name="satellite-dlls"></a>위성 DLL
 규칙에 따라 특정 로캘에 대한 리소스를 포함하는 VSPackage 위성 DLL은 *VSPackage* 디렉터리의 하위 디렉토리에 있습니다. 하위 디렉터리로 는 로캘 ID(LCID) 값에 해당합니다.

 [VSPackage관리](../../extensibility/managing-vspackages.md) 문서는 레지스트리 항목이 VSPackage의 위성 DLL을 실제로 찾는 위치를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 제어한다는 것을 나타냅니다. 그러나 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] LCID 값에 대 한 명명 된 하위 디렉터리에서 위성 DLL을 로드 하려고 합니다.

1. 기본 LCID(Visual Studio LCID; 예: 영어의 경우 *\1033)*

2. 기본 하위 언어가 있는 기본 LCID입니다.

3. 시스템 기본 LCID.

4. 기본 하위 언어를 가진 시스템 기본 LCID입니다.

5. 미국 영어 *(.\1033* 또는 *.\0x409).*

VSPackage DLL에 리소스와 **SatelliteDll\DllName** 레지스트리 입력 지점이 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 포함된 경우 위의 순서로 로드하려고 시도합니다.

## <a name="see-also"></a>참조
- [공유 및 버전 이면된 VSPackage 중에서 선택](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [VSPackage 관리](../../extensibility/managing-vspackages.md)
- [패키지 등록 관리](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)

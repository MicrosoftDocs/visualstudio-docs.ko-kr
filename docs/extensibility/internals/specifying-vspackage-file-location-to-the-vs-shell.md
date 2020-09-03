---
title: VS 셸에 VSPackage 파일 위치 지정 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f112da4e79bff06d12472f0af7a3fe47b2f25da4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704971"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>VSPackage 파일 위치를 VS Shell에 지정
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage를 로드 하기 위해 어셈블리 DLL을 찾을 수 있어야 합니다. 다음 표에서 설명 하는 것 처럼 다양 한 방법으로 찾을 수 있습니다.

| 메서드 | 설명 |
| - | - |
| CodeBase 레지스트리 키를 사용 합니다. | 코드 베이스 키는 정규화 된 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 파일 경로에서 VSPackage 어셈블리를 로드 하도록 지시 하는 데 사용할 수 있습니다. 키의 값은 DLL의 파일 경로 여야 합니다. 패키지 어셈블리를 로드 하는 것이 가장 좋은 방법입니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 이 기술을 "코드 베이스/개인 설치 디렉터리 기법"이 라고도 합니다. 등록 하는 동안 코드 베이스의 값은 형식의 인스턴스를 통해 등록 특성 클래스로 전달 됩니다 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> . |
| **PrivateAssemblies** 디렉터리에 DLL을 추가 합니다. | 어셈블리를 디렉터리의 **PrivateAssemblies** 하위 디렉터리에 저장 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 합니다. **PrivateAssemblies** 에 있는 어셈블리는 자동으로 검색 되지만 **참조 추가** 대화 상자에 표시 되지 않습니다. **PrivateAssemblies** 와 **publicassemblies** 간의 차이점은 **Publicassemblies** 의 어셈블리가 **참조 추가** 대화 상자에 열거 된다는 것입니다. "CodeBase/private 설치 디렉터리" 기술을 사용 하지 않도록 선택한 경우 **PrivateAssemblies** 디렉터리에를 설치 해야 합니다. |
| 강력한 이름의 어셈블리 및 어셈블리 레지스트리 키를 사용 합니다. | 어셈블리 키를 사용 하 여 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 강력한 이름의 VSPackage 어셈블리를 로드 하도록 명시적으로 지시할 수 있습니다. 키의 값은 어셈블리의 강력한 이름 이어야 합니다. |
| DLL을 **Publicassemblies** 디렉터리에 넣습니다. | 마지막으로 어셈블리를 **Publicassemblies** 하위 디렉터리에 배치할 수도 있습니다. **Publicassemblies** 에 있는 어셈블리는 자동으로 검색 되 고의 **참조 추가** 대화 상자에도 표시 됩니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .<br /><br /> VSPackage 어셈블리는 다른 VSPackage 개발자가 다시 사용 하기 위해 관리 되는 구성 요소를 포함 하는 경우에만 **publicassemblies** 디렉터리에 배치 해야 합니다. 대부분의 어셈블리는이 조건을 충족 하지 않습니다. |

> [!NOTE]
> 모든 종속 어셈블리에 대해 강력한 이름의 서명 된 어셈블리를 사용 합니다. 이러한 어셈블리는 사용자의 디렉터리 또는 GAC (전역 어셈블리 캐시)에도 설치 해야 합니다. 이렇게 하면 약한 이름 바인딩 이라고 하는 기본 파일 이름이 동일한 어셈블리와의 충돌을 방지할 수 있습니다.

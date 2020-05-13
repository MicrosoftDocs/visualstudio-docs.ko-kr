---
title: VS 셸에 VS패키지 파일 위치 지정 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704971"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>VSPackage 파일 위치를 VS Shell에 지정
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage를 로드할 어셈블리 DLL을 찾을 수 있어야 합니다. 다음 표에 설명된 대로 다양한 방법으로 찾을 수 있습니다.

| 방법 | 설명 |
| - | - |
| CodeBase 레지스트리 키를 사용합니다. | CodeBase 키를 사용하여 정규화된 파일 경로에서 VSPackage 어셈블리를 로드하도록 지시할 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 수 있습니다. 키값은 DLL의 파일 경로여야 합니다. 이것이 패키지 어셈블리를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 로드하는 가장 좋은 방법입니다. 이 기술을 "CodeBase/개인 설치 디렉터리 기술"이라고도 합니다. 등록 하는 동안 코드 베이스의 값 형식의 인스턴스를 통해 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> 등록 특성 클래스에 전달 됩니다. |
| DLL을 개인 **어셈블리** 디렉토리에 배치합니다. | 어셈블리를 디렉터리의 **사설 어셈블리** 하위 디렉터리에 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 배치합니다. **전용 어셈블리에** 있는 어셈블리는 자동으로 검색되지만 **참조 추가** 대화 상자에는 표시되지 않습니다. **Private 어셈블리와** **공용 어셈블리의** 차이점은 **Public 어셈블리의** 어셈블리가 **참조 추가** 대화 상자에서 열거된다는 점입니다. "CodeBase/개인 설치 디렉터리" 기술을 사용하지 않도록 선택한 경우 Private **Assemblies** 디렉터리에 설치해야 합니다. |
| 강력한 이름의 어셈블리와 어셈블리 레지스트리 키를 사용합니다. | 어셈블리 키를 사용하여 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 강력한 이름의 VSPackage 어셈블리를 로드하도록 명시적으로 지시할 수 있습니다. 키의 값은 어셈블리의 강력한 이름이어야 합니다. |
| DLL을 공용 **어셈블리** 디렉토리에 배치합니다. | 마지막으로 어셈블리를 **Public Assemblyies** 하위 디렉터리에도 배치할 수 있습니다. **Public 어셈블리에** 있는 어셈블리는 자동으로 검색되며 참조 **추가** 대화 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]상자에도 표시됩니다.<br /><br /> VSPackage 어셈블리는 다른 VSPackage 개발자가 다시 사용할 수 있는 관리되는 구성 요소가 포함된 경우에만 **Public어셈블리** 디렉토리에 배치해야 합니다. 대부분의 어셈블리가 이 기준을 충족하지 않습니다. |

> [!NOTE]
> 모든 종속 어셈블리에 대해 강력한 이름의 서명된 어셈블리를 사용합니다. 이러한 어셈블리는 사용자 고유의 디렉터리 또는 GAC(전역 어셈블리 캐시)에도 설치해야 합니다. 이렇게 하면 약자 바인딩이라고 하는 동일한 기본 파일 이름을 가진 어셈블리와의 충돌이 방지됩니다.

---
title: 윈도우 설치 프로그램 기본 사항 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aeea0b17a3c234bb7670642fb9ae0a442c9d60cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703412"
---
# <a name="windows-installer-basics"></a>Windows Installer 기본 사항
Windows 설치 관리자는 사용자의 컴퓨터에 응용 프로그램 이나 소프트웨어 제품을 설치 하 고 제거, Windows 설치 관리자 구성 요소 라는 단위로 이러한 작업을 수행 (WICs 또는 그냥 구성 요소 라고도). GUID는 Windows 설치 관리자를 사용하여 설치에 대한 설치 및 참조 계산의 기본 단위인 각 WIC를 식별합니다.

 Windows 설치 관리자에 대한 포괄적인 설명서는 플랫폼 SDK 항목인 [Windows 설치 관리자를](/previous-versions/2kt85ked(v=vs.120))참조하십시오.

## <a name="authoring-a-vspackage"></a>VS패키지 작성
 Windows Installer는 Windows Installer가 제품을 설치, 제거 또는 복구하고 설치 사용자 인터페이스(UI)를 실행하는 데 필요한 정보가 포함된 설치 패키지를 사용합니다. 각 설치 패키지에는 설치 데이터베이스, 요약 정보 스트림 및 설치의 다양한 부분에 대한 데이터 스트림이 포함된 .msi 파일이 포함되어 있습니다. 설치 프로그램을 사용하려면 설치를 작성해야 합니다. 설치 관리자는 구성 요소 개념을 중심으로 설치를 구성하고 설치에 대한 정보를 관계형 데이터베이스에 저장하므로 설치 패키지를 작성하는 프로세스에는 다음 단계가 광범위하게 수반됩니다.

1. 버전 관리 및 나란히 전략을 지원하도록 설정 작성을 계획합니다.

2. 사용자에게 표시할 기능을 식별합니다.

3. VSPackage 및 종속성을 구성 요소로 구성합니다.

4. 설치 데이터베이스를 정보로 채웁니다.

5. 설치 패키지의 유효성을 검사합니다.

   이 설명서는 주로 프로세스의 첫 번째 및 세 번째 단계와 관련이 있습니다. 이 단계에서 는 VSPackage 기능을 WIC로 구성하여 의 후속 버전을 고려하여 버전 전환 및 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]서비스 전략을 구성할 수 있습니다. 나머지 세 단계는 플랫폼 SDK의 Windows 설치 관리자 설명서에서 자세히 다룹니다.

## <a name="key-terms"></a>주요 용어
 다음은 Windows 설치 관리자 기술과 관련된 주요 용어에 대한 정의입니다.

 리소스 파일, 레지스트리 키, 바로 가기 등 컴퓨터에 설치할 수 있습니다. 이러한 리소스는 Windows 설치 관리자 구성 요소로 논리적으로 그룹화됩니다.

 WIC(Windows 설치 관리자 구성 요소) 단위로 설치 및 제거된 관련 리소스의 논리적 그룹을 나타내는 설치의 기본 단위입니다. Windows 설치 관리자 구성 요소는 고유한 구성 요소 ID 또는 GUID로 식별됩니다. 또한 Windows 설치 관리자는 WIC 수준에서 참조 카운트를 유지 관리합니다. 최대 버전 관리 유연성을 위해 지정된 WIC에 DLL과 같은 기본 리소스를 하나 만 포함하십시오. WIC를 식별하고 채우고 GUID를 제공하고 배포한 후에는 해당 구성을 변경할 수 없습니다. 자세한 내용은 [응용 프로그램을 구성 요소로 구성을](/windows/desktop/Msi/organizing-applications-into-components)참조하십시오.

 패키지(Redist 패키지) 이 파일이 가리킬 수 있는 .msi 파일 및 외부 소스 파일로 구성된 배포 단위입니다. 패키지에는 Windows Installer가 UI를 실행하고 응용 프로그램을 설치하거나 제거하는 데 필요한 모든 정보가 들어 있습니다.

 .msi 파일 응용 프로그램을 설치하는 데 필요한 지침과 데이터를 포함하는 COM 구조화 된 저장 파일. 모든 패키지에는 하나 이상의 .msi 파일이 포함되어 있습니다. .msi 파일에는 설치 프로그램 데이터베이스, 요약 정보 스트림 및 하나 이상의 변환 및 내부 원본 파일이 포함되어 있습니다. 설치할 파일은 캐비닛으로 압축하여 .msi 파일의 스트림에 저장하거나 소스 매체의 .msi 파일 외부에 저장, 압축 또는 압축되지 않은 파일을 저장할 수 있습니다. 자세한 내용은 [Windows 설치 관리자 파일 확장을](/windows/desktop/Msi/windows-installer-file-extensions)참조하십시오.

## <a name="windows-installer-rules-enforcement"></a>Windows 설치 관리자 규칙 적용
 두 가지 규칙 집합은 설치 구성 요소를 통해 리소스 배포를 결정합니다. 한 규칙 집합은 Windows Installer 자체에서 유지 관리되지만 두 번째 집합은 설치 작성자로 적용해야 합니다.

> [!NOTE]
> Windows 설치 관리자 규칙의 적용은 .msi 파일의 유효성 검사를 실행하는 경우에만 발생합니다. 그럼에도 불구하고 이러한 규칙을 모범 사례로 취급하라는 경고를 받습니다. 자세한 내용은 [설치 데이터베이스](/windows/desktop/Msi/validating-an-installation-database) 및 패키지 [유효성 검사](/windows/desktop/Msi/package-validation)유효성 검사 를 참조하십시오.

#### <a name="installer-enforced-rules"></a>설치 관리자 적용 규칙

- 지정된 구성 요소의 모든 파일을 동일한 디렉터리에 설치해야 합니다. 반대로 별도의 폴더에 설치된 파일은 별도의 구성 요소에 속해야 합니다.

- 구성 요소당 하나의 키 경로만 있을 수 있습니다. 키 경로는 단순히 전체 구성 요소를 나타내는 파일 또는 레지스트리 키입니다.

#### <a name="component-provider-responsibilities"></a>구성 요소 공급자 책임

- 후속 버전에서 별도로 제공될 수 있는 두 리소스는 별도의 구성 요소에 있어야 합니다. 리소스는 이러한 리소스가 별도로 발송되지 않을 것이라는 확신이 있는 경우에만 동일한 구성 요소로 그룹화되어야 합니다. 실제로 모든 기본 리소스(예: DLL)는 항상 별도의 WIC에 있는 것이 좋습니다. 자세한 내용은 [설치 관리자 구성 요소 정의를](/windows/desktop/Msi/defining-installer-components)참조하십시오.

- 버전이 있는 리소스는 두 개 이상의 WIC에 제공되어서는 안 됩니다.

## <a name="see-also"></a>참조
- [구성 요소 규칙이 깨지면 어떻게 됩니까?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)

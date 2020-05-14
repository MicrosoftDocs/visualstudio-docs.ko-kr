---
title: 부트스트래퍼 패키지 만들기
ms.date: 05/02/2018
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], prerequisites
- deploying applications [Visual Studio], custom prerequisites
- prerequisites, custom
- RedistList file
- custom prerequisites
- redistributables list
ms.assetid: ba1a785b-693d-446b-bcae-b88cadee73d1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f84f91ebedd47df8c0804adee35dcbec18d8551
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301010"
---
# <a name="create-bootstrapper-packages"></a>부트스트래퍼 패키지 만들기
설치 프로그램은 일반 설치 관리자로서 Windows Installer(*.msi*) 파일 및 실행 프로그램과 같은 재배포 가능 구성 요소를 검색 및 설치하도록 구성할 수 있습니다. 설치 관리자를 부트스트래퍼라고도 합니다. 구성 요소 설치를 관리하는 메타데이터를 지정하는 XML 매니페스트 집합을 통해 설치 프로그램을 프로그래밍합니다.  ClickOnce의 **필수 구성 요소** 대화 상자에 표시되는 각 재배포 가능 구성 요소 또는 필수 구성 요소는 부트스트랩래퍼 패키지입니다. 부트스트래퍼 패키지는 필수 구성 요소를 설치해야 하는 방법을 설명하는 매니페스트 파일이 포함된 파일과 디렉터리 그룹입니다.

부트스트래퍼는 먼저 필수 구성 요소가 이미 설치되었는지를 검색합니다. 필수 구성 요소가 설치되지 않은 경우 부트스트래퍼는 먼저 사용권 계약을 표시합니다. 그런 다음, 최종 사용자가 사용권 계약에 동의하면 필수 구성 요소 설치가 시작됩니다. 그렇지 않고 모든 필수 구성 요소가 검색되면 부트스트래퍼는 애플리케이션 설치 관리자만 시작합니다.

## <a name="create-custom-bootstrapper-packages"></a>사용자 지정 부트스트래퍼 패키지 만들기
Visual Studio에서 XML 편집기에서 부트스트랩 퍼미티지를 생성할 수 있습니다. 부트스트랩래퍼 패키지를 만드는 예제를 보려면 [연습: 개인 정보 보호 프롬프트를 사용하여 사용자 지정 부트스트랩래퍼 만들기를](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md)참조하십시오.

bootstrapper 패키지를 만들려면 제품 매니페스트를 만들고 구성 요소의 각 지역화된 버전에 대해 패키지 매니페스트도 만들어야 합니다.

* 제품 *매니페스트인 product.xml에는*패키지에 대한 언어 중립적 메타데이터가 포함되어 있습니다. 여기에는 재배포 가능 구성 요소의 지역화된 모든 버전에 공통적으로 적용되는 메타데이터가 포함됩니다.  이 파일을 만들려면 [방법: 제품 매니페스트 만들기](../deployment/how-to-create-a-product-manifest.md)를 참조하십시오.

* 패키지 매니페스트, *package.xml에는*언어별 메타데이터가 포함되어 있습니다. 일반적으로 지역화된 오류 메시지가 포함되어 있습니다. 구성 요소에는 해당 구성 요소의 각 지역화된 버전에 대한 패키지 매니페스트가 하나 이상 있어야 합니다. 이 파일을 만들려면 [방법: 패키지 매니페스트 만들기](../deployment/how-to-create-a-package-manifest.md)를 참조하십시오.

이러한 파일을 만든 후 제품 매니페스트 파일을 사용자 지정 부트스트래퍼에 대해 이름이 지정된 폴더에 저장합니다. 패키지 매니페스트 파일은 로캘에 대해 이름이 지정된 폴더에 저장합니다. 예를 들어 영어 재배포용 패키지 매니페스트 파일은 en 폴더에 저장합니다. 각 로캘(예: 일본어는 ja, 독일어는 de)에 대해 이 프로세스를 반복합니다. 최종 사용자 지정 부트스트래퍼 패키지는 다음과 같은 폴더 구조일 수 있습니다.

```
CustomBootstrapperPackage
  product.xml
  CustomBootstrapper.msi
  de
    eula.rtf
    package.xml
  en
    eula.rtf
    package.xml
  ja
    eula.rtf
    package.xml
```

다음으로 재배포 가능한 파일을 부트스래퍼 폴더 위치에 복사합니다. 자세한 내용은 [지역화된 부트스트랩래퍼 패키지 만들기 방법을](../deployment/how-to-create-a-localized-bootstrapper-package.md)참조하십시오.

```
*\Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper*
```

또는 이전 버전의 Visual Studio용

```
*\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

또는

```
*\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

다음 레지스트리 키에서 **Path** 값에서 bootstrapper 폴더 위치를 찾을 수도 있습니다.

```
*HKLM\Software\Microsoft\GenericBootstrapper*
```

64비트 시스템에서는 다음 레지스트리 키를 사용합니다.

```
*HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper*
```

각 재배포 가능 구성 요소는 packages 디렉터리 아래의 고유 하위 폴더에 표시됩니다. 제품 매니페스트 및 재배포 가능한 파일은 이 하위 폴더에 넣어야 합니다. 구성 요소 및 패키지 매니페스트의 지역화된 버전은 문화권 이름에 따라 명명된 하위 폴더에 넣어야 합니다.

이러한 파일을 부트스트래퍼 폴더에 복사하면 부트스트래퍼 패키지가 Visual Studio **필수 구성 요소** 대화 상자에 자동으로 표시됩니다. 사용자 지정 부트스트래퍼 패키지가 표시되지 않으면 **필수 구성 요소** 대화 상자를 닫았다가 다시 엽니다. 자세한 내용은 [필수 구성 조건 대화 상자를](../ide/reference/prerequisites-dialog-box.md)참조하십시오.

다음 테이블에는 부트스트래퍼가 자동으로 채우는 속성이 나와 있습니다.

|속성|Description|
|--------------|-----------------|
|ApplicationName|애플리케이션 이름입니다.|
|ProcessorArchitecture|실행 파일의 대상인 플랫폼의 단어당 비트 및 프로세서입니다. 여기에는 다음 값이 포함됩니다.<br /><br /> - Intel<br />- IA64<br />- AMD64|
|[Version9x](/windows/desktop/Msi/version9x)|Microsoft Windows 95, Windows 98 또는 Windows ME 운영 체제의 버전 번호. 버전의 구문은 Major.Minor.ServicePack입니다.|
|[VersionNT](/windows/desktop/Msi/versionnt)|Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 또는 Windows 7 운영 체제의 버전 번호. 버전의 구문은 Major.Minor.ServicePack입니다.|
|[VersionMSI](/windows/desktop/Msi/versionmsi)|설치 하는 동안 실행 하는 Windows 설치 관리자 어셈블리 (msi.dll)의 버전입니다.|
|[관리자 사용자](/windows/desktop/Msi/adminuser)|사용자에게 관리자 권한이 있으면 이 속성이 설정됩니다. 값은 true 또는 false입니다.|
|InstallMode|설치 모드는 구성 요소 설치를 시작해야 하는 위치를 나타냅니다. 여기에는 다음 값이 포함됩니다.<br /><br /> - HomeSite - 공급업체의 웹 사이트에서 필수 구성 요소를 설치합니다.<br />- SpecificSite - 선택한 위치에서 필수 구성 요소를 설치합니다.<br />- SameSite - 애플리케이션과 동일한 위치에서 필수 구성 요소를 설치합니다.|

## <a name="separate-redistributables-from-application-installations"></a>응용 프로그램 설치와 재배포 할 수 있는 개별
설치 프로젝트에서 재배포 가능 파일이 배포되지 않도록 지정할 수 있습니다. 이렇게 하려면 .NET Framework 디렉터리의 RedistList 폴더에 재배포 가능 파일 목록을 만듭니다.

`%ProgramFiles%\Microsoft.NET\RedistList`

재배포 가능한 목록은 다음 형식을 사용하여 이름을 지정해야 하는 XML * \<파일입니다:\< 회사 이름>. 구성 요소 이름>. 레디스트리스트.xml*. 예를 들어 Acme에서 만든 Datawidgets 구성 요소의 경우 *Acme.DataWidgets.RedistList.xml*을 사용합니다. 아래에는 재배포 가능 파일 목록 내용의 예제가 나와 있습니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<FileList Redist="Acme.DataWidgets" >
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />
</FileList>
```

## <a name="see-also"></a>참고 항목
- [방법: ClickOnce 애플리케이션을 사용하여 필수 구성 요소 설치](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [필수 구성 조건 대화 상자](../ide/reference/prerequisites-dialog-box.md)
- [제품 및 패키지 스키마 참조](../deployment/product-and-package-schema-reference.md)
- [Visual Studio 2005 부트스트랩래퍼를 사용하여 설치를 시작하십시오.](https://msdn.microsoft.com/magazine/cc163899.aspx)

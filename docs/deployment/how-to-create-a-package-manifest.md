---
title: 방법-패키지 매니페스트 만들기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc3a1263136fe4c50b2c7020e1557a7a693691b6
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382525"
---
# <a name="how-to-create-a-package-manifest"></a>방법: 패키지 매니페스트 만들기
응용 프로그램에 대 한 필수 구성 요소를 배포 하기 위해 부트스트래퍼 패키지를 사용할 수 있습니다. 부트스트래퍼 패키지는 단일 제품 매니페스트 파일을 포함 하지만 각 로캘에 대 한 패키지 매니페스트를 포함 합니다. 서로 다른 지역화 된 버전에서 공유 되는 기능은 제품 매니페스트로 이동 해야 합니다.

 제품 매니페스트에 대 한 자세한 내용은 [방법: 제품 매니페스트 만들기](../deployment/how-to-create-a-product-manifest.md)를 참조 하세요.

## <a name="create-the-package-manifest"></a>패키지 매니페스트 만들기

#### <a name="to-create-the-package-manifest"></a>패키지 매니페스트를 만들려면

1. 부트스트래퍼 패키지에 대 한 디렉터리를 만듭니다. 이 예에서는 *C:\package*를 사용 합니다.

2. 로캘 이름 (예: 영어의 경우 *en* )을 사용 하 여 하위 디렉터리를 만듭니다.

3. Visual Studio에서 *package.xml*이라는 XML 파일을 만들고 *C:\package\en* 폴더에 저장 합니다.

4. XML을 추가 하 여 부트스트래퍼 패키지의 이름,이 지역화 된 패키지 매니페스트의 culture 및 선택적 라이선스 계약을 나열 합니다. 다음 XML에서는 및 변수를 사용 합니다 .이 변수는 `DisplayName` `Culture` 이후 요소에 정의 되어 있습니다.

    ```xml
    <Package
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
        Name="DisplayName"
        Culture="Culture"
        LicenseAgreement="eula.txt">
    ```

5. XML을 추가 하 여 로캘별 디렉터리에 있는 모든 파일을 나열 합니다. 다음 XML은 **en** 로캘에 적용 되는 *eula.txt* 라는 파일을 사용 합니다.

    ```xml
    <PackageFiles>
      <PackageFile Name="eula.txt"/>
    </PackageFiles>
    ```

6. 부트스트래퍼 패키지에 대 한 지역화할 수 있는 문자열을 정의 하는 XML을 추가 합니다. 다음 XML은 **en** 로캘에 대 한 오류 문자열을 추가 합니다.

    ```xml
      <Strings>
        <String Name="DisplayName">Custom Bootstrapper Package</String>
        <String Name="CultureName">en</String>
        <String Name="NotAnAdmin">You must be an administrator to install
    this package.</String>
        <String Name="GeneralFailure">A general error has occurred while
    installing this package.</String>
    </Strings>
    ```

7. *C:\package* 폴더를 Visual Studio 부트스트래퍼 디렉터리에 복사 합니다. Visual Studio 2010의 경우이 디렉터리는 *Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* 디렉터리입니다.

## <a name="example"></a>예제
 패키지 매니페스트에는 오류 메시지, 소프트웨어 사용 조건 및 언어 팩과 같은 로캘별 정보가 포함 되어 있습니다.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Package
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
  Name="DisplayName"
  Culture="Culture"
  LicenseAgreement="eula.txt">

  <PackageFiles>
    <PackageFile Name="eula.txt"/>
  </PackageFiles>

  <Strings>
    <String Name="DisplayName">Custom Bootstrapper Package</String>
    <String Name="Culture">en</String>
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>
    <String Name="GeneralFailure">A general error has occurred while
installing this package.</String>
  </Strings>
</Package>
```

## <a name="see-also"></a>추가 정보
- [제품 및 패키지 스키마 참조](../deployment/product-and-package-schema-reference.md)
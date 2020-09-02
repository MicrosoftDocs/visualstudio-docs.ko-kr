---
title: '방법: 제품 매니페스트 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- product files [ClickOnce]
- product files [Windows Installer]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper package
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 73e2c3f2c9736fd762a9e763827ed641ea5069f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153821"
---
# <a name="how-to-create-a-product-manifest"></a>방법: 제품 매니페스트 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

응용 프로그램에 대 한 필수 구성 요소를 배포 하기 위해 부트스트래퍼 패키지를 만들 수 있습니다. 부트스트래퍼 패키지는 단일 제품 매니페스트 파일을 포함 하지만 각 로캘에 대 한 패키지 매니페스트를 포함 합니다. 패키지 매니페스트에는 패키지의 지역화 관련 측면이 포함 됩니다. 여기에는 문자열, 최종 사용자 사용권 계약 및 언어 팩이 포함 됩니다.  
  
 제품 매니페스트에 대 한 자세한 내용은 [방법: 패키지 매니페스트 만들기](../deployment/how-to-create-a-package-manifest.md)를 참조 하세요.  
  
## <a name="creating-the-product-manifest"></a>제품 매니페스트 만들기  
  
#### <a name="to-create-the-product-manifest"></a>제품 매니페스트를 만들려면  
  
1. 부트스트래퍼 패키지에 대 한 디렉터리를 만듭니다. 이 예제에서는 C:\package.를 사용 합니다.  
  
2. Visual Studio에서 라는 새 XML 파일을 만들고 `product.xml` C:\package 폴더에 저장 합니다.  
  
3. 다음 XML을 추가 하 여 패키지에 대 한 XML 네임 스페이스 및 제품 코드를 설명 합니다. 제품 코드를 패키지의 고유 식별자로 바꿉니다.  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4. XML을 추가 하 여 패키지에 종속성이 있는지를 지정 합니다. 이 예제에서는 Microsoft Windows Installer 3.1에 대 한 종속성을 사용 합니다.  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5. XML을 추가 하 여 부트스트래퍼 패키지에 있는 모든 파일을 나열 합니다. 이 예에서는 CorePackage.msi 패키지 파일 이름을 사용 합니다.  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6. CorePackage.msi 파일을 C:\package 폴더로 복사 하거나 이동 합니다.  
  
7. 부트스트래퍼 명령을 사용 하 여 패키지를 설치 하는 XML을 추가 합니다. 부트스트래퍼는 자동으로 설치 되는 **/qn** 플래그를 .msi 파일에 자동으로 추가 합니다. 파일이 .exe 인 경우 부트스트래퍼는 셸을 사용 하 여 .exe 파일을 실행 합니다. 다음 XML은 CorePackage.msi 인수를 표시 하지 않지만 Arguments 특성에 명령줄 인수를 넣을 수 있습니다.  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8. 다음 XML을 추가 하 여이 부트스트래퍼 패키지가 설치 되어 있는지 확인 합니다. 제품 코드를 재배포 가능 구성 요소에 대 한 GUID로 바꿉니다.  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. 부트스트래퍼 구성 요소가 이미 설치 되어 있는지 여부에 따라 부트스트래퍼 동작을 변경 하는 XML을 추가 합니다. 구성 요소가 설치 되어 있으면 부트스트래퍼 패키지가 실행 되지 않습니다. 다음 XML은이 구성 요소에 관리자 권한이 필요 하기 때문에 현재 사용자가 관리자 인지 확인 합니다.  
  
    ```  
    <InstallConditions>  
        <BypassIf   
           Property="IsMsiInstalled"   
           Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
            Compare="ValueNotEqualTo" Value="True"  
            String="NotAnAdmin"/>  
    </InstallConditions>  
    ```  
  
10. 설치에 성공 하 고 다시 부팅이 필요한 경우에는 종료 코드를 설정 하는 XML을 추가 합니다. 다음 XML은 부트스트래퍼가 패키지 설치를 계속할 수 없음을 나타내는 오류 및 장애 복구 종료 코드를 보여 줍니다.  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. 다음 XML을 추가 하 여 부트스트래퍼 명령에 대 한 섹션을 종료 합니다.  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. C:\package 폴더를 Visual Studio 부트스트래퍼 디렉터리로 이동 합니다. Visual Studio 2010의 경우이 디렉터리는 Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages 디렉터리입니다.  
  
## <a name="example"></a>예  
 제품 매니페스트에는 사용자 지정 필수 구성 요소에 대 한 설치 지침이 포함 되어 있습니다.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Product  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  ProductCode="Custom.Bootstrapper.Package">  
  
  <RelatedProducts>  
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
  </RelatedProducts>  
  
  <PackageFiles>  
    <PackageFile Name="CorePackage.msi"/>  
  </PackageFiles>  
  
  <InstallChecks>  
    <MsiProductCheck Product="IsMsiInstalled"   
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
  </InstallChecks>  
  
  <Commands>  
    <Command PackageFile="CorePackage.msi" Arguments="">  
  
      <InstallConditions>  
        <BypassIf Property="IsMsiInstalled"  
          Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
          Compare="ValueNotEqualTo" Value="True"  
         String="NotAnAdmin"/>  
      </InstallConditions>  
  
      <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
      </ExitCodes>  
    </Command>  
  </Commands>  
</Product>  
```  
  
## <a name="see-also"></a>관련 항목  
 [제품 및 패키지 스키마 참조](../deployment/product-and-package-schema-reference.md)

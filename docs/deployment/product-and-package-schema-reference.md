---
title: 제품 및 패키지 스키마 참조 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.CircularIncludes
- MSBuild.ResolveManifestFiles.PublishFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce, product and package files
- Windows Installer, product and package files
- product files [ClickOnce]
- ClickOnce, bootstrapper elements
- package files [Windows Installer]
- product files [Windows Installer]
- package files [ClickOnce]
- Windows Installer, bootstrapper elements
ms.assetid: 5a74878f-b896-4cca-b968-98d00fe78fb0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1570aa3d4ea72dc1d133ce3096e1726fa1ffb782
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66745621"
---
# <a name="product-and-package-schema-reference"></a>제품 및 패키지 스키마 참조
*제품 파일* 은 응용 프로그램에 필요한 모든 외부 종속성을 설명 하는 XML 매니페스트입니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . 외부 종속성의 예로는 .NET Framework 및 MDAC (Microsoft Data Access Components)가 있습니다. 패키지 파일은 제품 파일과 유사 하지만, 지역화 된 어셈블리, 사용권 계약 및 설명서와 같이 종속성의 문화권 종속 구성 요소를 설치 하는 데 사용 됩니다.

 제품 및 패키지 파일은 최상위 `Product` 또는 요소로 구성 되며 `Package` , 각 요소에는 다음 요소가 포함 되어 있습니다.

|요소|설명|특성|
|-------------|-----------------|----------------|
|[\<Product> 요소](../deployment/product-element-bootstrapper.md)|제품 파일의 최상위 수준 요소입니다.|없음|
|[\<Package> 요소](../deployment/package-element-bootstrapper.md)|패키지 파일에 대 한 최상위 수준 요소입니다.|`Culture`<br /><br /> `Name`<br /><br /> `EULA`|
|[\<RelatedProducts> 요소](../deployment/relatedproducts-element-bootstrapper.md)|제품 파일의 선택적 요소입니다. 이 제품이 설치 되거나 종속 되는 다른 제품은 다음과 동일 합니다.|없음|
|[\<InstallChecks> 요소](../deployment/installchecks-element-bootstrapper.md)|필수적 요소입니다. 설치 하는 동안 로컬 컴퓨터에서 수행 하는 종속성 검사를 나열 합니다.|없음|
|[\<Commands> 요소](../deployment/commands-element-bootstrapper.md)|필수적 요소입니다.  에 설명 된 대로 하나 이상의 설치 검사 `InstallChecks` 를 실행 하 고, 검사에 실패할 경우 설치할 패키지를 나타냅니다.|없음|
|[\<PackageFiles> 요소](../deployment/packagefiles-element-bootstrapper.md)|필수적 요소입니다. 이 설치 프로세스에서 설치할 수 있는 패키지를 나열 합니다.|없음|
|[\<Strings> 요소](../deployment/strings-element-bootstrapper.md)|필수적 요소입니다. 제품 이름 및 오류 문자열의 지역화 된 버전을 저장 합니다.|None|

## <a name="remarks"></a>설명
 패키지 스키마는 자체 하드 코딩 된 논리를 포함 하는 MS Build 부트스트래핑 작업에 의해 생성 된 스텁 프로그램인 *Setup.exe*에서 사용 됩니다. 스키마는 설치 프로세스의 모든 측면을 구동 합니다.

 `InstallChecks` setup.exe에서 지정 된 패키지의 존재를 위해 수행 해야 하는 테스트입니다. `PackageFiles` 지정 된 테스트가 실패 하는 경우 설치 프로세스에서 설치 해야 할 수 있는 모든 패키지를 나열 합니다. 명령 아래의 각 명령 항목은에서 설명 하는 테스트 중 하나 `InstallChecks` 를 실행 하 고 `PackageFile` 테스트가 실패할 경우 실행할를 지정 합니다. 요소를 사용 하 여 `Strings` 제품 이름 및 오류 메시지를 지역화할 수 있습니다. 그러면 단일 설치 이진을 사용 하 여 원하는 수의 언어로 응용 프로그램을 설치할 수 있습니다.

## <a name="example"></a>예
 다음 코드 예제에서는 .NET Framework를 설치 하기 위한 전체 제품 파일을 보여 줍니다.

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Product
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
  ProductCode="Microsoft.Net.Framework.2.0"
>

    <RelatedProducts>
        <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />
    </RelatedProducts>

    <!-- Defines list of files to be copied on build -->
    <PackageFiles>
        <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>
        <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>
        <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>
        <PackageFile Name="dotnetchk.exe"/>
    </PackageFiles>

    <InstallChecks>
        <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />
        <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />
    </InstallChecks>

    <!-- Defines how to invoke the setup for the .NET Framework redist -->
    <!-- TODO: Needs EstrimatedTempSpace, LogFile, and an update of EstimatedDiskSpace -->
    <Commands Reboot="Defer">
        <Command PackageFile="instmsia.exe"
                 Arguments= ' /q /c:"msiinst /delayrebootq"'
                 EstimatedInstallSeconds="20" >
            <InstallConditions>
                <BypassIf Property="VersionNT" Compare="ValueExists"/>
                <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>
            </InstallConditions>
            <ExitCodes>
                <ExitCode Value="0" Result="SuccessReboot"/>
                <ExitCode Value="1641" Result="SuccessReboot"/>
                <ExitCode Value="3010" Result="SuccessReboot"/>
                <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />
            </ExitCodes>
        </Command>
        <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"
                 Arguments= '/quiet /norestart'
                 EstimatedInstallSeconds="20" >
          <InstallConditions>
              <BypassIf Property="Version9x" Compare="ValueExists"/>
              <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>
              <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>
              <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>
          </InstallConditions>
          <ExitCodes>
              <ExitCode Value="0" Result="Success"/>
              <ExitCode Value="1641" Result="SuccessReboot"/>
              <ExitCode Value="3010" Result="SuccessReboot"/>
              <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />
          </ExitCodes>
        </Command>
        <Command PackageFile="dotnetfx.exe"
             Arguments=' /q:a /c:"install /q /l"'
             EstimatedInstalledBytes="21000000"
             EstimatedInstallSeconds="300">

            <!-- These checks determine whether the package is to be installed -->
            <InstallConditions>
                <!-- Either of these properties indicates the .NET Framework is already installed -->
                <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>

                <!-- Block install if user does not have admin privileges -->
                <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>

                <!-- Block install on Windows 95 -->
                <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>

                <!-- Block install on Windows 2000 SP 2 or less -->
                <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>

                <!-- Block install if Internet Explorer 5.01 or greater is not present -->
                <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />
                <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />

                <!-- Block install if the platform is not x86 -->
                <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />
            </InstallConditions>

            <ExitCodes>
                <ExitCode Value="0" Result="Success"/>
                <ExitCode Value="3010" Result="SuccessReboot"/>
                <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>
                <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>
                <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>
                <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>
                <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>
                <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>
                <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />
            </ExitCodes>

        </Command>
    </Commands>
</Product>
```

## <a name="see-also"></a>추가 정보
- [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md)
- [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)
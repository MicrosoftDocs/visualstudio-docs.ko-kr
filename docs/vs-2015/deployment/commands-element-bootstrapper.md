---
title: '&lt;Commands &gt; 요소 (부트스트래퍼) | Microsoft Docs'
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
- <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: af10c9e0b26a6ef2c8e7a98bc345b8e86017682b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205342"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;Commands &gt; 요소 (부트스트래퍼)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

요소는 `Commands` 요소 아래의 요소에서 설명 하는 테스트 `InstallChecks` 를 구현 하 고 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 테스트가 실패할 경우 부트스트래퍼가 설치 해야 하는 패키지를 선언 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Commands  
    Reboot  
>  
    <Command  
        PackageFile  
        Arguments  
        EstimatedInstallSeconds  
        EstimatedDiskBytes  
        EstimatedTempBytes  
        Log  
    >  
        <InstallConditions>  
            <BypassIf   
                Property  
                Compare  
                Value  
                Schedule  
            />  
            <FailIf   
                Property  
                Compare  
                Value  
                String  
                Schedule  
            />  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode   
                Value  
                Result  
                String  
            />  
        </ExitCodes>  
    </Command>  
</Commands>  
```  
  
## <a name="elements-and-attributes"></a>요소 및 특성  
 `Commands`요소가 필요 합니다. 요소에는 다음 특성이 있습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`Reboot`|선택 사항입니다. 패키지가 다시 시작 종료 코드를 반환 하는 경우 시스템을 다시 시작할지 여부를 결정 합니다. 다음 목록에서는 유효한 값을 보여 줍니다.<br /><br /> `Defer`. 이후 시간까지 다시 시작이 지연 됩니다.<br /><br /> `Immediate`. 패키지 중 하나가 다시 시작 종료 코드를 반환한 경우 즉시 다시 시작 됩니다.<br /><br /> `None`. 다시 시작 요청을 무시 합니다.<br /><br /> 기본값은 `Immediate`입니다.|  
  
## <a name="command"></a>명령  
 `Command` 요소는 `Commands` 요소의 자식 요소입니다. `Commands`요소는 하나 이상의 요소를 포함할 수 있습니다 `Command` . 요소에는 다음 특성이 있습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`PackageFile`|필수 요소. 에서 지정 된 하나 이상의 조건이 false를 반환 하는 경우 설치할 패키지의 이름입니다 `InstallConditions` . 요소를 사용 하 여 패키지를 동일한 파일에 정의 해야 합니다 `PackageFile` .|  
|`Arguments`|선택 사항입니다. 패키지 파일에 전달할 명령줄 인수 집합입니다.|  
|`EstimatedInstallSeconds`|선택 사항입니다. 패키지를 설치 하는 데 걸리는 예상 시간 (초)입니다. 이 값은 부트스트래퍼가 사용자에 게 표시 하는 진행률 표시줄의 크기를 결정 합니다. 기본값은 0 이며,이 경우 시간 예측이 지정 되지 않습니다.|  
|`EstimatedDiskBytes`|선택 사항입니다. 설치가 완료 된 후 패키지가 차지할 디스크 공간의 예상 크기 (바이트)입니다. 이 값은 부트스트래퍼가 사용자에 게 표시 하는 하드 디스크 공간 요구 사항에 사용 됩니다. 기본값은 0 이며,이 경우 부트스트래퍼는 하드 디스크 공간 요구 사항을 표시 하지 않습니다.|  
|`EstimatedTempBytes`|선택 사항입니다. 패키지에 필요한 임시 디스크 공간의 예상 크기 (바이트)입니다.|  
|`Log`|선택 사항입니다. 패키지가 생성 하는 로그 파일에 대 한 경로로, 패키지의 루트 디렉터리를 기준으로 합니다.|  
  
## <a name="installconditions"></a>InstallConditions  
 요소는 `InstallConditions` 요소의 자식입니다 `Command` . 각 `Command` 요소에는 최대 하나의 요소만 있을 수 있습니다 `InstallConditions` . 요소가 없는 경우 `InstallConditions` 에 지정 된 패키지는 `Condition` 항상를 실행 합니다.  
  
## <a name="bypassif"></a>BypassIf  
 `BypassIf`요소는 `InstallConditions` 요소의 자식 이며 명령이 실행 되지 않아야 하는 긍정 조건을 설명 합니다. 각 `InstallConditions` 요소에는 0 개 이상의 요소가 있을 수 있습니다 `BypassIf` .  
  
 `BypassIf` 에는 다음과 같은 특성이 있습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`Property`|필수 요소. 테스트할 속성의 이름입니다. 속성은 이전에 요소의 자식에 의해 정의 되어 있어야 합니다 `InstallChecks` . 자세한 내용은 [\<InstallChecks> 요소](../deployment/installchecks-element-bootstrapper.md)를 참조하세요.|  
|`Compare`|필수 요소. 수행할 비교의 형식입니다. 다음 목록에서는 유효한 값을 보여 줍니다.<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|필수 요소. 속성과 비교할 값입니다.|  
|`Schedule`|선택 사항입니다. `Schedule`이 규칙을 평가 해야 하는 경우를 정의 하는 태그의 이름입니다.|  
  
## <a name="failif"></a>FailIf  
 `FailIf`요소는 `InstallConditions` 요소의 자식 이며 설치를 중지 하는 긍정 조건을 설명 합니다. 각 `InstallConditions` 요소에는 0 개 이상의 요소가 있을 수 있습니다 `FailIf` .  
  
 `FailIf` 에는 다음과 같은 특성이 있습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`Property`|필수 요소. 테스트할 속성의 이름입니다. 속성은 이전에 요소의 자식에 의해 정의 되어 있어야 합니다 `InstallChecks` . 자세한 내용은 [\<InstallChecks> 요소](../deployment/installchecks-element-bootstrapper.md)를 참조하세요.|  
|`Compare`|필수 요소. 수행할 비교의 형식입니다. 다음 목록에서는 유효한 값을 보여 줍니다.<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|필수 요소. 속성과 비교할 값입니다.|  
|`String`|선택 사항입니다. 실패 시 사용자에 게 표시할 텍스트입니다.|  
|`Schedule`|선택 사항입니다. `Schedule`이 규칙을 평가 해야 하는 경우를 정의 하는 태그의 이름입니다.|  
  
## <a name="exitcodes"></a>ExitCodes  
 요소는 `ExitCodes` 요소의 자식입니다 `Command` . `ExitCodes`요소는 하나 이상의 `ExitCode` 요소를 포함 하며,이 요소는 설치에서 패키지의 종료 코드에 대 한 응답으로 수행 해야 하는 작업을 결정 합니다. `ExitCode`요소 아래에는 선택적 요소가 하나만 있을 수 있습니다 `Command` . `ExitCodes`에는 특성이 없습니다.  
  
## <a name="exitcode"></a>ExitCode  
 요소는 `ExitCode` 요소의 자식입니다 `ExitCodes` . `ExitCode`요소는 패키지의 종료 코드에 대 한 응답으로 설치에서 수행 해야 하는 작업을 결정 합니다. `ExitCode` 에는 자식 요소가 없고 다음과 같은 특성이 있습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`Value`|필수 요소. 이 요소가 적용 되는 종료 코드 값 `ExitCode` 입니다.|  
|`Result`|필수 요소. 설치에서이 종료 코드에 반응 하는 방법입니다. 다음 목록에서는 유효한 값을 보여 줍니다.<br /><br /> `Success`. 패키지를 성공적으로 설치 된 것으로 플래그를 합니다.<br /><br /> `SuccessReboot`. 패키지를 성공적으로 설치 하 고 시스템을 다시 시작 하도록 지시 합니다.<br /><br /> `Fail`. 패키지에 오류가 발생 한 것으로 플래그를 합니다.<br /><br /> `FailReboot`. 패키지를 실패 한 것으로 플래그 하 고 시스템을 다시 시작 하도록 지시 합니다.|  
|`String`|선택 사항입니다. 이 종료 코드에 대 한 응답으로 사용자에 게 표시할 값입니다.|  
|`FormatMessageFromSystem`|선택 사항입니다. 종료 코드에 해당 하는 시스템 제공 오류 메시지를 사용할지 또는에 제공 된 값을 사용할지를 결정 합니다 `String` . 유효한 값은 `true` 시스템 제공 오류를 사용 하는 이며,에서 제공 하는 문자열을 사용 하는 것을 의미 `false` `String` 합니다. 기본값은 `false`입니다. 이 속성이이 `false` 고 `String` 설정 되지 않은 경우 시스템 제공 오류가 사용 됩니다.|  
  
## <a name="example"></a>예  
 다음 코드 예제에서는 .NET Framework 2.0를 설치 하기 위한 명령을 정의 합니다.  
  
```  
<Commands Reboot="Immediate">  
    <Command PackageFile="instmsia.exe"  
             Arguments= ' /q /c:"msiinst /delayrebootq"'  
             EstimatedInstallSeconds="20" >  
        <InstallConditions>  
           <BypassIf Property="VersionNT" Compare="ValueExists"/>  
             BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>  
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
  
            <!-- Block install if user does not have adminpermissions -->  
            <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
  
            <!-- Block install on Windows 95 -->  
            <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>  
  
            <!-- Block install on Windows 2000 SP 2 or less -->  
            <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>  
  
            <!-- Block install if Internet Explorer 5.01 or later is not present -->  
            <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />  
            <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />  
  
            <!-- Block install if the operating system does not support x86 -->  
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
```  
  
## <a name="see-also"></a>관련 항목  
 [제품 및 패키지 스키마 참조](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks> 요소](../deployment/installchecks-element-bootstrapper.md)

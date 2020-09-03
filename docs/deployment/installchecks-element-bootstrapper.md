---
title: '&lt;InstallChecks &gt; 요소 (부트스트래퍼) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <InstallChecks> element [bootstrapper]
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7ba4da072a586bdc09993b77200a769be3940ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85536307"
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;InstallChecks &gt; 요소 (부트스트래퍼)
`InstallChecks`요소는 응용 프로그램에 대 한 모든 적절 한 필수 구성 요소가 설치 되었는지 확인 하기 위해 로컬 컴퓨터에 대해 다양 한 테스트를 시작 하도록 지원 합니다.

## <a name="syntax"></a>Syntax

```xml
<InstallChecks>
    <AssemblyCheck
        Property
        Name
        PublicKeyToken
        Version
        Language
        ProcessorArchitecture
    />
    <RegistryCheck
        Property
        Key
        Value
    />
    <ExternalCheck
        PackageFile
        Property
        Arguments
    />
    <FileCheck
        Property
        FileName
        SearchPath
        SpecialFolder
        SearchDepth
    />
    <MsiProductCheck
        Property
        Product
        Feature
    />
    <RegistryFileCheck
        Property
        Key
        Value
        FileName
        SearchDepth
    />
</InstallChecks>
```

## <a name="assemblycheck"></a>AssemblyCheck
 이 요소는의 선택적 자식 요소입니다 `InstallChecks` . 각 인스턴스에 대해 `AssemblyCheck` 부트스트래퍼는 요소로 식별 되는 어셈블리가 GAC (전역 어셈블리 캐시)에 있는지 확인 합니다. 여기에는 요소가 없으며 다음과 같은 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`Property`|필수 요소. 결과를 저장할 속성의 이름입니다. 요소의 자식인 요소 아래의 테스트에서이 속성을 참조할 수 있습니다 `InstallConditions` `Command` . 자세한 내용은 [\<Commands> 요소](../deployment/commands-element-bootstrapper.md)를 참조하세요.|
|`Name`|필수 요소. 확인할 어셈블리의 정규화 된 이름입니다.|
|`PublicKeyToken`|필수 요소. 강력한 이름의 어셈블리와 연결 된 공개 키의 약식 형식입니다. GAC에 저장 된 모든 어셈블리에는 이름, 버전 및 공개 키가 있어야 합니다.|
|`Version`|필수 요소. 어셈블리의 버전입니다.<br /><br /> 버전 번호의 형식은 \<*major version*> ... \<*minor version*> \<*build version*> \<*revision version*> 입니다.|
|`Language`|선택 사항입니다. 지역화 된 어셈블리의 언어입니다. 기본값은 `neutral`입니다.|
|`ProcessorArchitecture`|선택 사항입니다. 이 설치의 대상 컴퓨터 프로세서입니다. 기본값은 `msil`입니다.|

## <a name="externalcheck"></a>ExternalCheck
 이 요소는의 선택적 자식 요소입니다 `InstallChecks` . 각 인스턴스에 대해 `ExternalCheck` 부트스트래퍼는 개별 프로세스에서 명명 된 외부 프로그램을 실행 하 고가 나타내는 속성에 종료 코드를 저장 합니다 `Property` . `ExternalCheck` 는 복잡 한 종속성 검사를 구현 하는 데 유용 하며, 구성 요소가 있는지 확인 하는 유일한 방법은이를 인스턴스화하는 것입니다.

 `ExternalCheck` 에는 요소가 없으며 다음과 같은 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`Property`|필수 요소. 결과를 저장할 속성의 이름입니다. 요소의 자식인 요소 아래의 테스트에서이 속성을 참조할 수 있습니다 `InstallConditions` `Command` . 자세한 내용은 [\<Commands> 요소](../deployment/commands-element-bootstrapper.md)를 참조하세요.|
|`PackageFile`|필수 요소. 실행할 외부 프로그램입니다. 프로그램은 설치 배포 패키지의 일부 여야 합니다.|
|`Arguments`|선택 사항입니다. 는로 명명 된 실행 파일에 명령줄 인수를 제공 `PackageFile` 합니다.|

## <a name="filecheck"></a>FileCheck
 이 요소는의 선택적 자식 요소입니다 `InstallChecks` . 부트스트래퍼는의 각 인스턴스에 대해 `FileCheck` 명명 된 파일이 있는지 여부를 확인 하 고 파일의 버전 번호를 반환 합니다. 파일에 버전 번호가 없으면 부트스트래퍼는로 명명 된 속성을 `Property` 0으로 설정 합니다. 파일이 없는 경우 `Property` 값으로 설정 되지 않습니다.

 `FileCheck` 에는 요소가 없으며 다음과 같은 특성이 있습니다.

| 특성 | 설명 |
|-----------------| - |
| `Property` | 필수 요소. 결과를 저장할 속성의 이름입니다. 요소의 자식인 요소 아래의 테스트에서이 속성을 참조할 수 있습니다 `InstallConditions` `Command` . 자세한 내용은 [\<Commands> 요소](../deployment/commands-element-bootstrapper.md)를 참조하세요. |
| `FileName` | 필수 요소. 찾을 파일의 이름입니다. |
| `SearchPath` | 필수 요소. 파일을 찾을 디스크나 폴더입니다. 이 할당 된 경우이 경로는 상대 경로 여야 합니다. `SpecialFolder` 그렇지 않으면 절대 경로 여야 합니다. |
| `SpecialFolder` | 선택 사항입니다. Windows 또는에 대 한 특별 한 의미가 있는 폴더입니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . 기본값은 절대 경로로 해석 하는 것입니다 `SearchPath` . 유효한 값은 다음과 같습니다.<br /><br /> `AppDataFolder`. 현재 사용자와 관련 된이 응용 프로그램에 대 한 응용 프로그램 데이터 폴더입니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .<br /><br /> `CommonAppDataFolder`. 모든 사용자가 사용 하는 응용 프로그램 데이터 폴더입니다.<br /><br /> `CommonFilesFolder`. 현재 사용자의 Common Files 폴더입니다.<br /><br /> `LocalDataAppFolder`. 로밍되지 않는 응용 프로그램에 대 한 데이터 폴더입니다.<br /><br /> `ProgramFilesFolder`. 32 비트 응용 프로그램에 대 한 표준 Program Files 폴더입니다.<br /><br /> `StartUpFolder`. 시스템 시작 시 시작 된 모든 응용 프로그램을 포함 하는 폴더입니다.<br /><br /> `SystemFolder`. 32 비트 시스템 Dll이 포함 된 폴더입니다.<br /><br /> `WindowsFolder`. Windows 시스템 설치를 포함 하는 폴더입니다.<br /><br /> `WindowsVolume`. Windows 시스템 설치를 포함 하는 드라이브 또는 파티션입니다. |
| `SearchDepth` | 선택 사항입니다. 명명 된 파일에 대 한 하위 폴더를 검색 하는 수준입니다. 검색은 깊이 우선 합니다. 기본값은 0 이며,이는 검색을 및 SearchPath로 지정 된 최상위 폴더로 제한 `SpecialFolder` 합니다 **SearchPath**. |

## <a name="msiproductcheck"></a>MsiProductCheck
 이 요소는의 선택적 자식 요소입니다 `InstallChecks` . 각 인스턴스에 대해 `MsiProductCheck` 부트스트래퍼는 지정 된 Microsoft Windows Installer 설치가 완료 될 때까지 실행 되었는지 여부를 확인 합니다. 속성 값은 설치 된 제품의 상태에 따라 설정 됩니다. 양수 값은 제품이 설치 되어 있음을 나타내고 0 또는-1은 해당 제품이 설치 되어 있지 않음을 나타냅니다. 자세한 내용은 Windows Installer SDK 함수 MsiQueryFeatureState를 참조 하세요. . 컴퓨터에 Windows Installer 설치 되어 있지 않으면 `Property` 이 설정 되지 않습니다.

 `MsiProductCheck` 에는 요소가 없으며 다음과 같은 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`Property`|필수 요소. 결과를 저장할 속성의 이름입니다. 요소의 자식인 요소 아래의 테스트에서이 속성을 참조할 수 있습니다 `InstallConditions` `Command` . 자세한 내용은 [\<Commands> 요소](../deployment/commands-element-bootstrapper.md)를 참조하세요.|
|`Product`|필수 요소. 설치 된 제품에 대 한 GUID입니다.|
|`Feature`|선택 사항입니다. 설치 된 응용 프로그램의 특정 기능에 대 한 GUID입니다.|

## <a name="registrycheck"></a>RegistryCheck
 이 요소는의 선택적 자식 요소입니다 `InstallChecks` . 부트스트래퍼는의 각 인스턴스에 대해 지정 된 레지스트리 키가 있는지 또는 지정 된 값이 있는지 여부를 `RegistryCheck` 확인 합니다.

 `RegistryCheck` 에는 요소가 없으며 다음과 같은 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`Property`|필수 요소. 결과를 저장할 속성의 이름입니다. 요소의 자식인 요소 아래의 테스트에서이 속성을 참조할 수 있습니다 `InstallConditions` `Command` . 자세한 내용은 [\<Commands> 요소](../deployment/commands-element-bootstrapper.md)를 참조하세요.|
|`Key`|필수 요소. 레지스트리 키의 이름입니다.|
|`Value`|선택 사항입니다. 검색할 레지스트리 값의 이름입니다. 기본값은 기본값의 텍스트를 반환 하는 것입니다. `Value` 는 문자열 또는 DWORD 여야 합니다.|

## <a name="registryfilecheck"></a>RegistryFileCheck
 이 요소는의 선택적 자식 요소입니다 `InstallChecks` . 각 인스턴스에 대해 `RegistryFileCheck` 부트스트래퍼는 지정 된 파일의 버전을 검색 하 고, 먼저 지정 된 레지스트리 키에서 파일의 경로를 검색 하려고 시도 합니다. 이는 레지스트리의 값으로 지정 된 디렉터리에서 파일을 조회 하려는 경우에 특히 유용 합니다.

 `RegistryFileCheck` 에는 요소가 없으며 다음과 같은 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`Property`|필수 요소. 결과를 저장할 속성의 이름입니다. 요소의 자식인 요소 아래의 테스트에서이 속성을 참조할 수 있습니다 `InstallConditions` `Command` . 자세한 내용은 [\<Commands> 요소](../deployment/commands-element-bootstrapper.md)를 참조하세요.|
|`Key`|필수 요소. 레지스트리 키의 이름입니다. 특성이 설정 되지 않은 경우 해당 값은 파일에 대 한 경로로 해석 됩니다 `File` . 이 키가 없으면이 `Property` 설정 되지 않습니다.|
|`Value`|선택 사항입니다. 검색할 레지스트리 값의 이름입니다. 기본값은 기본값의 텍스트를 반환 하는 것입니다. `Value` 는 문자열 이어야 합니다.|
|`FileName`|선택 사항입니다. 파일의 이름입니다. 지정 된 경우 레지스트리 키에서 가져온 값은 디렉터리 경로로 간주 되 고이 이름이 추가 됩니다. 지정 하지 않으면 레지스트리에서 반환 된 값이 파일의 전체 경로로 간주 됩니다.|
|`SearchDepth`|선택 사항입니다. 명명 된 파일에 대 한 하위 폴더를 검색 하는 수준입니다. 검색은 깊이 우선 합니다. 기본값은 0으로, 레지스트리 키의 값으로 지정 된 최상위 폴더로 검색을 제한 합니다.|

## <a name="remarks"></a>설명
 아래 요소는 `InstallChecks` 실행할 테스트를 정의 하지만 실행 하지는 않습니다. 테스트를 실행 하려면 `Command` 요소 아래에 요소를 만들어야 합니다 `Commands` .

## <a name="example"></a>예
 다음 코드 예제에서는 `InstallChecks` .NET Framework에 대 한 제품 파일에서 사용 되는 요소를 보여 줍니다.

```xml
<InstallChecks>
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />
</InstallChecks>
```

## <a name="installconditions"></a>InstallConditions
 `InstallChecks`가 평가 되 면 속성을 생성 합니다. 그런 다음에서 속성을 사용 `InstallConditions` 하 여 패키지를 설치, 무시 또는 실패 여부를 결정 합니다. 다음 표에는이 나열 되어 `InstallConditions` 있습니다.

|조건|설명|
|-|-|
|`FailIf`|`FailIf`조건이 true로 평가 되는 경우 패키지는 실패 합니다. 나머지 조건은 평가 되지 않습니다.|
|`BypassIf`|`BypassIf`조건이 true로 평가 되는 경우 패키지는 무시 됩니다. 나머지 조건은 평가 되지 않습니다.|

## <a name="predefined-properties"></a>미리 정의 된 속성
 다음 표에서는 및 요소를 보여 줍니다 `BypassIf` `FailIf` .

|속성|참고|가능한 값|
|--------------|-----------|---------------------|
|`Version9X`|Windows 9X 운영 체제의 버전 번호입니다.|4.10 = Windows 98|
|`VersionNT`|Windows NT 기반 운영 체제의 버전 번호입니다.|Major.Minor.ServicePack<br /><br /> 5.0 = Windows 2000<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Professional SP2<br /><br /> 5.2.0 = Windows Server 2003|
|`VersionNT64`|64 비트 Windows NT 기반 운영 체제의 버전 번호입니다.|앞에서 설명한 것과 동일 합니다.|
|`VersionMsi`|Windows Installer 서비스의 버전 번호입니다.|2.0 = Windows Installer 2.0|
|`AdminUser`|사용자에 게 Windows NT 기반 운영 체제에 대 한 관리자 권한이 있는지 여부를 지정 합니다.|0 = 관리자 권한 없음<br /><br /> 1 = 관리자 권한|

 예를 들어 Windows 95를 실행 하는 컴퓨터에서 설치를 차단 하려면 다음과 같은 코드를 사용 합니다.

```xml
<!-- Block install on Windows 95 -->
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>
```

## <a name="see-also"></a>추가 정보
- [\<Commands> 요소인](../deployment/commands-element-bootstrapper.md)
- [제품 및 패키지 스키마 참조](../deployment/product-and-package-schema-reference.md)
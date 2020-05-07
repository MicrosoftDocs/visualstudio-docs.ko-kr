---
title: 속성 함수 | Microsoft Docs
ms.date: 02/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5f1d34a6d21e6d4f413275ee21651feb7ec3dec
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586683"
---
# <a name="property-functions"></a>속성 함수

속성 함수는 MSBuild 속성 정의에 표시되는 .NET Framework 메서드에 대한 호출입니다. 작업과 달리 속성 함수는 대상 외부에서 사용할 수 있으며, 대상이 실행되기 전에 평가됩니다.

MSBuild 작업을 사용하지 않고도 시스템 시간을 읽고 문자열을 비교하며 정규식을 일치시키고 빌드 스크립트의 다른 작업을 수행할 수 있습니다. MSBuild는 문자열을 숫자로, 숫자를 문자열로 변환하려고 하며, 필요한 경우 다른 변환을 수행합니다.

속성 기능에서 반환된 문자열 값에서는 [특수 문자](msbuild-special-characters.md)가 이스케이프됩니다. 프로젝트 파일에 직접 입력된 것처럼 값을 처리하려면 `$([MSBuild]::Unescape())`를 사용하여 특수 문자를 이스케이프 해제합니다.

속성 함수는 .NET Framework 4 이상에서 사용할 수 있습니다.

## <a name="property-function-syntax"></a>속성 함수 구문

다음과 같은 세 가지 종류의 속성 함수가 있으며, 각 함수의 구문은 서로 다릅니다.

- 문자열(인스턴스) 속성 함수
- 정적 속성 함수
- MSBuild 속성 함수

### <a name="string-property-functions"></a>문자열 속성 함수

모든 빌드 속성 값은 문자열 값입니다. 문자열(인스턴스) 메서드를 사용하여 모든 속성 값에 대해 수행할 수 있습니다. 예를 들어, 다음 코드를 사용하여 전체 경로를 나타내는 빌드 속성에서 드라이브 이름(처음 세 문자)을 추출할 수 있습니다.

```
$(ProjectOutputFolder.Substring(0,3))
```

### <a name="static-property-functions"></a>정적 속성 함수

빌드 스크립트에서 많은 시스템 클래스의 정적 속성 및 메서드에 액세스할 수 있습니다. 정적 속성값을 가져오려면 다음 구문을 사용합니다. 여기서 \<Class>는 시스템 클래스의 이름이고 \<Property>는 속성의 이름입니다.

```
$([Class]::Property)
```

예를 들어, 다음 코드를 사용하여 빌드 속성을 현재 날짜 및 시간으로 설정할 수 있습니다.

```xml
<Today>$([System.DateTime]::Now)</Today>
```

정적 메서드를 호출하려면 다음 구문을 사용합니다. 여기서 \<Class>는 시스템 클래스의 이름이고 \<Method>는 메서드의 이름이며 (\<Parameters>)는 메서드의 매개 변수 목록입니다.

```
$([Class]::Method(Parameters))
```

예를 들어, 빌드 속성을 새 GUID로 설정하려면 다음 스크립트를 사용하면 됩니다.

```xml
<NewGuid>$([System.Guid]::NewGuid())</NewGuid>
```

정적 속성 함수에는 다음과 같은 시스템 클래스의 모든 정적 메서드 또는 속성을 사용할 수 있습니다.

- System.Byte
- System.Char
- System.Convert
- System.DateTime
- System.Decimal
- System.Double
- System.Enum
- System.Guid
- System.Int16
- System.Int32
- System.Int64
- System.IO.Path
- System.Math
- System.Runtime.InteropServices.OSPlatform
- System.Runtime.InteropServices.RuntimeInformation
- System.UInt16
- System.UInt32
- System.UInt64
- System.SByte
- System.Single
- System.String
- System.StringComparer
- System.TimeSpan
- System.Text.RegularExpressions.Regex
- System.UriBuilder
- System.Version
- Microsoft.Build.Utilities.ToolLocationHelper

또한 다음 정적 메서드 및 속성을 사용할 수 있습니다.

- System.Environment::CommandLine
- System.Environment::ExpandEnvironmentVariables
- System.Environment::GetEnvironmentVariable
- System.Environment::GetEnvironmentVariables
- System.Environment::GetFolderPath
- System.Environment::GetLogicalDrives
- System.IO.Directory::GetDirectories
- System.IO.Directory::GetFiles
- System.IO.Directory::GetLastAccessTime
- System.IO.Directory::GetLastWriteTime
- System.IO.Directory::GetParent
- System.IO.File::Exists
- System.IO.File::GetCreationTime
- System.IO.File::GetAttributes
- System.IO.File::GetLastAccessTime
- System.IO.File::GetLastWriteTime
- System.IO.File::ReadAllText

### <a name="calling-instance-methods-on-static-properties"></a>정적 속성에 대한 인스턴스 메서드 호출

개체 인스턴스를 반환하는 정적 속성에 액세스하는 경우 해당 개체의 인스턴스 메서드를 호출할 수 있습니다. 인스턴스 메서드를 호출하려면 다음 구문을 사용합니다. 여기서 \<Class>는 시스템 클래스의 이름이고 \<Property>는 속성의 이름이며 \<Method>는 메서드의 이름이고, (\<Parameters>)는 메서드의 매개 변수 목록입니다.

```
$([Class]::Property.Method(Parameters))
```

클래스의 이름은 네임스페이스를 포함하는 정규화된 이름이어야 합니다.

예를 들어, 다음 코드를 사용하여 빌드 속성을 현재 날짜 오늘로 설정할 수 있습니다.

```xml
<Today>$([System.DateTime]::Now.ToString('yyyy.MM.dd'))</Today>
```

### <a name="msbuild-property-functions"></a>MSBuild 속성 함수

빌드의 여러 정적 메서드에 액세스하여 산술, 비트 논리 및 이스케이프 문자 지원을 제공할 수 있습니다. 다음 구문을 사용하여 이러한 메서드에 액세스합니다. 여기서 \<Method>는 메서드의 이름이고 (\<Parameters>)는 메서드의 매개 변수 목록입니다.

```
$([MSBuild]::Method(Parameters))
```

예를 들어, 숫자 값을 가지는 두 속성을 함께 추가하려면 다음 코드를 사용합니다.

```
$([MSBuild]::Add($(NumberOne), $(NumberTwo)))
```

다음은 MSBuild 속성 함수 목록입니다.

|함수 시그니처|설명|
|------------------------|-----------------|
|double Add(double a, double b)|두 double을 더합니다.|
|long Add(long a, long b)|두 long을 더합니다.|
|double Subtract(double a, double b)|한 double에서 다른 한 double을 뺍니다.|
|long Subtract(long a, long b)|한 long에서 다른 한 long을 뺍니다.|
|double Multiply(double a, double b)|두 double을 곱합니다.|
|long Multiply(long a, long b)|두 long을 곱합니다.|
|double Divide(double a, double b)|한 double을 다른 한 double로 나눕니다.|
|long Divide(long a, long b)|한 long을 다른 한 long으로 나눕니다.|
|double Modulo(double a, double b)|한 double을 다른 한 double로 나눈 나머지입니다.|
|long Modulo(long a, long b)|한 long을 다른 한 long으로 나눈 나머지입니다.|
|string Escape(string unescaped)|MSBuild 이스케이프 규칙에 따라 문자열을 이스케이프합니다.|
|string Unescape(string escaped)|MSBuild 이스케이프 규칙에 따라 문자열을 이스케이프하지 않습니다.|
|int BitwiseOr(int first, int second)|first와 second에 대해 비트 `OR`을 수행합니다(first &#124; second).|
|int BitwiseAnd(int first, int second)|first와 second에 대해 비트 `AND`를 수행합니다(first & second).|
|int BitwiseXor(int first, int second)|first와 second에 대해 비트 `XOR`를 수행합니다(first ^ second).|
|int BitwiseNot(int first)|비트 `NOT`을 수행합니다(~first).|
|bool IsOsPlatform(string platformString)|현재 OS 플랫폼이 `platformString`인지 여부를 지정합니다. `platformString`은 <xref:System.Runtime.InteropServices.OSPlatform>의 멤버여야 합니다.|
|bool IsOSUnixLike()|현재 OS가 Unix 시스템인 경우 True입니다.|
|string NormalizePath(params string[] path)|제공된 경로의 정규화된 전체 경로를 가져오고 해당 경로에 현재 운영 체제에 대한 정확한 디렉터리 구분 문자가 있는지 확인합니다.|
|string NormalizeDirectory(params string[] path)|제공된 디렉터리의 정규화된 전체 경로를 가져오고 해당 경로에 현재 운영 체제에 대한 정확한 디렉터리 구분 문자와 후행 슬래시가 있는지 확인합니다.|
|string EnsureTrailingSlash(string path)|제공된 경로에 후행 슬래시가 없으면 후행 슬래시를 추가합니다. 경로가 빈 문자열이면 수정하지 않습니다.|
|string GetPathOfFileAbove(string file, string startingDirectory)|현재 빌드 파일 위치 위 디렉터리 구조에서 또는 지정된 경우 `startingDirectory`를 기반으로 파일의 전체 경로를 검색하여 반환합니다.|
|GetDirectoryNameOfFileAbove(string startingDirectory, string fileName)|지정된 디렉터리에서 또는 해당 디렉터리 위 디렉터리 구조의 위치에서 파일의 디렉터리를 찾아 반환합니다.|
|string MakeRelative(string basePath, string path)|`path`를 `basePath`의 상대 경로로 설정합니다. `basePath`는 절대 디렉터리여야 합니다. 상대 경로로 설정할 수 없는 `path`는 반환된 축자입니다. `Uri.MakeRelativeUri`와 비슷합니다.|
|string ValueOrDefault(string conditionValue, string defaultValue)|‘conditionValue’ 매개 변수가 비어 있는 경우에만 ‘defaultValue’ 매개 변수로 문자열을 반환하고, 비어 있지 않으면 conditionValue 값을 반환합니다.|

## <a name="nested-property-functions"></a>중첩 속성 함수

다음 예제에서 보여 주는 것처럼, 보다 복잡한 함수를 형성하기 위해 속성 함수를 결합할 수 있습니다.

```
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

이 예제에서는 <xref:System.IO.FileAttributes> 경로에 의해 지정된 파일의 `Archive``tempFile` 비트 값(32 또는 0)을 반환합니다. 열거형 데이터 값은 속성 함수 내에 이름으로 나타날 수 없습니다. 대신 숫자 값(32)을 사용해야 합니다.

메타데이터도 중첩 속성 함수에 나타날 수 있습니다. 자세한 내용은 [일괄 처리](../msbuild/msbuild-batching.md)를 참조하세요.

## <a name="msbuild-doestaskhostexist"></a>MSBuild DoesTaskHostExist

MSBuild의 `DoesTaskHostExist` 속성 함수는 작업 호스트가 현재 지정된 런타임 및 아키텍처 값에 대해 설치되었는지 여부를 반환합니다.

이 속성 함수의 구문은 다음과 같습니다.

```
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>MSBuild EnsureTrailingSlash

MSBuild의 `EnsureTrailingSlash` 속성 함수는 후행 슬래시(없는 경우)를 추가합니다.

이 속성 함수의 구문은 다음과 같습니다.

```
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```

## <a name="msbuild-getdirectorynameoffileabove"></a>MSBuild GetDirectoryNameOfFileAbove

MSBuild `GetDirectoryNameOfFileAbove` 속성 함수는 경로의 현재 디렉터리 위에 있는 디렉터리에서 파일을 찾습니다.

 이 속성 함수의 구문은 다음과 같습니다.

```
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```

 다음 코드는 이 구문의 예제입니다.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>MSBuild GetPathOfFileAbove

MSBuild의 `GetPathOfFileAbove` 속성 함수는 현재 디렉터리 위 디렉터리 구조에 있는 지정된 파일의 경로를 반환합니다. 다음을 호출하는 것과 기능적으로 동일합니다.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
```

이 속성 함수의 구문은 다음과 같습니다.

```
$([MSBuild]::GetPathOfFileAbove(dir.props))
```

## <a name="msbuild-getregistryvalue"></a>MSBuild GetRegistryValue

MSBuild `GetRegistryValue` 속성 함수는 레지스트리 키 값을 반환합니다. 이 함수는 두 개의 인수(키 이름 및 값 이름)를 사용하고 레지스트리의 값을 반환합니다. 값 이름을 지정하지 않은 경우 기본값이 반환됩니다.

다음 예제에서는 이 함수를 사용하는 방법을 보여 줍니다.

```
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

## <a name="msbuild-getregistryvaluefromview"></a>MSBuild GetRegistryValueFromView

MSBuild `GetRegistryValueFromView` 속성 함수는 레지스트리 키, 값 및 순서가 지정된 하나 이상의 레지스트리 보기를 고려하여 시스템 레지스트리 데이터를 가져옵니다. 키 및 값은 발견될 때까지 각 레지스트리 보기에서 순서대로 검색됩니다.

이 속성 함수의 구문은 다음과 같습니다.

```
[MSBuild]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)
```

Windows 64비트 운영 체제는 32비트 애플리케이션에 대한 **HKEY_LOCAL_MACHINE\SOFTWARE** 레지스트리 보기를 제공하는 **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node** 레지스트리 키를 유지 관리합니다.

기본적으로 WOW64에서 실행되는 32비트 애플리케이션은 32비트 레지스트리 보기에 액세스하고 64비트 애플리케이션은 64비트 레지스트리 보기에 액세스합니다.

다음과 같은 레지스트리 보기를 사용할 수 있습니다.

|레지스트리 보기|정의|
|-------------------|----------------|
|RegistryView.Registry32|32비트 애플리케이션 레지스트리 보기입니다.|
|RegistryView.Registry64|64비트 애플리케이션 레지스트리 보기입니다.|
|RegistryView.Default|애플리케이션이 실행되고 있는 프로세스와 일치하는 레지스트리 보기입니다.|

다음은 예제입니다.

 ```
$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))
```

는 **ReferenceAssemblies** 키의 **SLRuntimeInstallPath** 데이터를 가져오고, 먼저 64비트 레지스트리 보기에서 찾은 다음, 32비트 레지스트리 보기에서 찾습니다.

## <a name="msbuild-makerelative"></a>MSBuild MakeRelative

MSBuild `MakeRelative` 속성 함수는 첫 번째 경로를 기준으로 하여 두 번째 경로의 상대 경로를 반환합니다. 각 경로는 파일 또는 폴더일 수 있습니다.

이 속성 함수의 구문은 다음과 같습니다.

```
$([MSBuild]::MakeRelative($(FileOrFolderPath1), $(FileOrFolderPath2)))
```

다음 코드는 이 구문의 예제입니다.

```xml
<PropertyGroup>
    <Path1>c:\users\</Path1>
    <Path2>c:\users\username\</Path2>
</PropertyGroup>

<Target Name = "Go">
    <Message Text ="$([MSBuild]::MakeRelative($(Path1), $(Path2)))" />
    <Message Text ="$([MSBuild]::MakeRelative($(Path2), $(Path1)))" />
</Target>

<!--
Output:
   username\
   ..\
-->
```

## <a name="msbuild-valueordefault"></a>MSBuild ValueOrDefault

MSBuild `ValueOrDefault` 속성 함수는 첫 번째 인수가 null이거나 비어 있지 않은 한 첫 번째 인수를 반환합니다. 첫 번째 인수가 null이거나 비어 있으면 함수는 두 번째 인수를 반환합니다.

다음 예제에서는 이 함수를 사용하는 방법을 보여 줍니다.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <Value1>$([MSBuild]::ValueOrDefault('$(UndefinedValue)', 'a'))</Value1>
        <Value2>$([MSBuild]::ValueOrDefault('b', '$(Value1)'))</Value2>
    </PropertyGroup>

    <Target Name="MyTarget">
        <Message Text="Value1 = $(Value1)" />
        <Message Text="Value2 = $(Value2)" />
    </Target>
</Project>

<!--
Output:
  Value1 = a
  Value2 = b
-->
```

## <a name="msbuild-condition-functions"></a>MSBuild 조건 함수

`Exists` 및 `HasTrailingSlash` 함수는 속성 함수가 아닙니다. `Condition` 특성과 함께 사용할 수 있습니다. [MSBuild 조건](msbuild-conditions.md)을 참조하세요.

## <a name="see-also"></a>참조

- [MSBuild 속성](../msbuild/msbuild-properties.md)

- [MSBuild 개요](../msbuild/msbuild.md)

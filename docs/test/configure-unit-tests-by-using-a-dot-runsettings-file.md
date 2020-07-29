---
title: .runsettings 파일을 사용하여 단위 테스트 구성
ms.date: 07/15/2020
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: f638d60b7bd4416bb7a19cc960cac1159c755ab3
ms.sourcegitcommit: cb0c6e55ae560960a493df9ab56e3e9d9bc50100
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86972298"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>*.runsettings* 파일을 사용하여 단위 테스트 구성

*.runsettings* 파일을 사용하여 Visual Studio의 단위 테스트를 구성할 수 있습니다. 예를 들어, 테스트가 실행되는 .NET 버전, 테스트 결과 디렉터리 또는 테스트 실행 중에 수집되는 데이터를 변경할 수 있습니다. *.runsettings* 파일은 [코드 검사 분석](../test/customizing-code-coverage-analysis.md)을 사용자 지정하는 데 자주 사용됩니다.

실행 설정 파일을 사용하면 Azure Test Plans 또는 TFS(Team Foundation Server)를 통해 [명령줄](vstest-console-options.md), IDE 또는 [빌드 워크플로](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)에서 실행되는 테스트를 구성할 수 있습니다.

실행 설정 파일은 선택 사항입니다. 특별한 구성이 필요하지 않으면 *.runsettings* 파일이 필요하지 않습니다.

## <a name="create-a-run-settings-file-and-customize-it"></a>실행 설정 파일 만들기 및 사용자 지정

1. 실행 설정 파일을 솔루션에 추가합니다. **솔루션 탐색기**의 솔루션 바로 가기 메뉴에서 **추가** > **새 항목**, **XML File**을 차례로 선택합니다. 파일을 *test.runsettings* 등의 이름으로 저장합니다.

   > [!TIP]
   > 확장명으로 *.runsettings*를 사용하면 파일 이름은 아무런 상관이 없습니다.

2. [예제 *.runsettings 파일](#example-runsettings-file)에서 콘텐츠를 추가하고, 이후 섹션의 설명에 따라 요구 사항에 맞게 사용자 지정합니다.

3. 다음 방법 중 하나를 사용하여 원하는 *.runsettings 파일을 지정합니다.

   - [Visual Studio IDE](#specify-a-run-settings-file-in-the-ide)
   - [명령줄](#specify-a-run-settings-file-from-the-command-line)
   - Azure Test Plans 또는 TFS(Team Foundation Server)를 사용하여 [워크플로를 빌드](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)합니다.

4. 사용자 지정 실행 설정을 사용하는 단위 테스트를 실행합니다.

::: moniker range="vs-2017"

IDE에서 사용자 지정 설정을 끄고 켜려는 경우 **테스트** > **테스트 설정** 메뉴에서 파일을 선택 취소하거나 선택합니다.

![Visual Studio 2017에서 사용자 지정 설정 파일이 있는 테스트 설정 메뉴](../test/media/codecoverage-settingsfile.png)

::: moniker-end

::: moniker range=">=vs-2019"

IDE에서 사용자 지정 설정을 끄고 켜려는 경우 **테스트** 메뉴에서 파일을 선택 취소하거나 선택합니다.

::: moniker-end

> [!TIP]
> 솔루션에서 *.runsettings* 파일을 둘 이상 만들고, 필요에 따라 활성 테스트 설정 파일로 하나를 선택할 수 있습니다.

## <a name="specify-a-run-settings-file-in-the-ide"></a>IDE에서 실행 설정 파일 지정

사용 가능한 메서드는 Visual Studio 버전에 따라 다릅니다.

::: moniker range="vs-2017"
IDE에서 실행 설정 파일을 지정하려면 **테스트** > **테스트 설정** > **테스트 설정 파일 선택**을 선택한 다음, *.runsettings* 파일을 선택합니다.

![Visual Studio 2017에서 테스트 설정 파일 메뉴 선택](media/select-test-settings-file.png)

테스트 설정 메뉴에 파일이 나타나고 해당 파일을 선택 또는 선택 취소할 수 있습니다. 파일이 선택된 상태에서 **코드 검사 분석**을 사용할 때마다 실행 설정 파일이 적용됩니다.
::: moniker-end

::: moniker range=">=vs-2019"

### <a name="visual-studio-2019-version-164-and-later"></a>Visual Studio 2019 버전 16.4 이상

Visual Studio 2019 버전 16.4 이상에서 실행 설정 파일을 지정하는 세 가지 방법은 다음과 같습니다.

- [실행 설정 자동 검색](#autodetect-the-run-settings-file)
- [실행 설정 수동 설정](#manually-select-the-run-settings-file)
- [빌드 속성 설정](#set-a-build-property)

#### <a name="autodetect-the-run-settings-file"></a>실행 설정 파일 자동 검색

실행 설정 파일을 자동 검색하려면 솔루션 루트에 저장합니다.

실행 설정 파일의 자동 검색을 사용하도록 설정하면 이 파일의 설정이 모든 테스트 실행에 적용됩니다. 다음 두 가지 방법을 사용하여 runsettings 파일 자동 검색을 켤 수 있습니다.
  
- **도구** > **옵션** > **테스트** > **runsettings 파일 자동 검색** 선택

   ![Visual Studio 2019의 runsettings 파일 자동 검색 옵션](media/vs-2019/auto-detect-runsettings-tools-window.png)
      
- **테스트** > **실행 설정 구성** > **runsettings 파일 자동 검색** 선택
    
   ![Visual Studio 2019의 runsettings 파일 자동 검색 메뉴](media/vs-2019/auto-detect-runsettings-menu.png)

#### <a name="manually-select-the-run-settings-file"></a>실행 설정 파일 수동 선택

IDE에서는 **테스트** > **실행 설정 구성** > **솔루션 전체의 runsettings 파일 선택**을 선택한 후 *.runsettings* 파일을 선택합니다.

   - 이 파일은 솔루션 루트에 있는 *.runsettings* 파일(있는 경우)을 재정의하며 모든 테스트 실행에 적용됩니다.  
   - 이 파일 선택은 로컬에서만 지속됩니다.

![Visual Studio 2019의 솔루션 전체의 runsettings 파일 선택 메뉴](media/vs-2019/select-solution-settings-file.png)

#### <a name="set-a-build-property"></a>빌드 속성 설정

프로젝트 파일 또는 Directory.Build.props 파일을 통해 프로젝트에 빌드 속성을 추가합니다. 프로젝트의 실행 설정 파일은 **RunSettingsFilePath** 속성을 통해 지정됩니다.

- 프로젝트 수준 실행 설정은 현재 C#, VB, C++ 및 F# 프로젝트에서 지원됩니다.
- 프로젝트에 지정된 파일이 솔루션에 지정된 다른 실행 설정 파일을 재정의합니다.
- [이 MSBuild 속성](https://docs.microsoft.com/visualstudio/msbuild/msbuild-reserved-and-well-known-properties?view=vs-2019)을 사용하여 runsettings 파일 경로를 지정할 수 있습니다. 

프로젝트에 대한 *.runsettings* 파일을 지정하는 예제:
    
```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RunSettingsFilePath>$(MSBuildProjectDirectory)\example.runsettings</RunSettingsFilePath>
  </PropertyGroup>
  ...
</Project>
```

### <a name="visual-studio-2019-version-163-and-earlier"></a>Visual Studio 2019 버전 16.3 이하

IDE에서 실행 설정 파일을 지정하려면 **테스트** > **테스트 설정 파일 선택**을 선택합니다. *.runsettings* 파일을 찾아 선택합니다.

![Visual Studio 2019에서 테스트 설정 파일 메뉴 선택](media/vs-2019/select-settings-file.png)

테스트 메뉴에 파일이 나타나고 해당 파일을 선택 또는 선택 취소할 수 있습니다. 파일이 선택된 상태에서 **코드 검사 분석**을 사용할 때마다 실행 설정 파일이 적용됩니다.
::: moniker-end

## <a name="specify-a-run-settings-file-from-the-command-line"></a>명령줄에서 실행 설정 파일 지정

명령줄에서 테스트를 실행하려면 *vstest.console.exe*를 사용하고, **/Settings** 매개 변수를 통해 설정 파일을 지정합니다.

1. Visual Studio용 [개발자 명령 프롬프트](/dotnet/framework/tools/developer-command-prompt-for-vs)를 엽니다.

2. 다음과 유사한 명령을 입력합니다.

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

   또는

   ```cmd
   vstest.console.exe --settings:test.runsettings test.dll
   ```

자세한 내용은 [MSTest.exe 명령줄 옵션](vstest-console-options.md)을 참조하세요.

## <a name="the-runsettings-file"></a>*.runsettings 파일

*.runsettings 파일은 **RunSettings** 요소 내에 다양한 구성 요소를 포함하는 XML 파일입니다. 다음 섹션에서는 여러 요소에 대해 자세히 설명합니다. 전체 샘플은 [예제 *.runsettings 파일](#example-runsettings-file)을 참조하세요.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- configuration elements -->
</RunSettings>
```

각 구성 요소는 기본값이 있으므로 선택 사항입니다.

## <a name="runconfiguration-element"></a>RunConfiguration 요소

```xml
<RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <ResultsDirectory>.\TestResults</ResultsDirectory>
    <TargetPlatform>x86</TargetPlatform>
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
    <TestSessionTimeout>10000</TestSessionTimeout>
</RunConfiguration>
```

**RunConfiguration** 요소는 다음과 같은 요소를 포함할 수 있습니다.

|노드|기본값|값|
|-|-|-|
|**MaxCpuCount**|1|이 설정은 단위 테스트를 실행하는 경우 시스템에서 사용 가능한 코어를 사용하여 병렬 테스트 실행의 정도를 제어합니다. 테스트 실행 엔진이 사용 가능한 각 코어에서 별도의 프로세스로 시작되며, 실행할 테스트가 있는 컨테이너를 각 코어에 제공합니다. 컨테이너는 어셈블리, DLL 또는 관련 아티팩트일 수 있습니다. 테스트 컨테이너는 예약 단위입니다. 각 컨테이너에서 테스트는 테스트 프레임워크에 따라 실행됩니다. 많은 컨테이너가 있는 경우 프로세스가 컨테이너 내의 테스트 실행을 마치면 사용 가능한 다음 컨테이너가 제공됩니다.<br /><br />MaxCpuCount는 다음과 같을 수 있습니다.<br /><br />n, 여기서 1 <= n <= 코어 수이며, 최대 n개의 프로세스가 시작됩니다.<br /><br />n, 여기서 n = 다른 모든 값이 되며, 시작되는 프로세스의 수는 사용 가능한 최대 코어 수가 될 수 있습니다. 예를 들어 n=0을 설정하면 플랫폼에서는 환경을 기반으로 시작할 최적의 프로세스 수를 자동으로 결정할 수 있습니다.|
|**ResultsDirectory**||테스트 결과가 배치될 디렉터리입니다. 경로는 .runsettings 파일을 포함하는 디렉터리를 기준으로 합니다.|
|**TargetFrameworkVersion**|Framework40|`FrameworkCore10`은 .NET Core 소스, `FrameworkUap10`은 UWP 기반 소스, `Framework45`는 .NET Framework 4.5 이상, `Framework40`은 .NET Framework 4.0, `Framework35`는 .NET Framework 3.5를 나타냅니다.<br /><br />이 설정은 테스트를 검색하고 실행하는 데 사용할 단위 테스트 프레임워크의 버전을 지정합니다. 이 버전은 단위 테스트 프로젝트의 빌드 속성에 지정하는 .NET 플랫폼의 버전과 다를 수 있습니다.<br /><br />*.runsettings* 파일에서 `TargetFrameworkVersion` 요소를 생략하면, 플랫폼이 빌드된 이진 파일을 기준으로 프레임워크 버전을 자동으로 결정합니다.|
|**TargetPlatform**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|false|false, true|
|**TestAdaptersPaths**||TestAdapters가 있는 디렉터리에 대한 하나 이상의 경로|
|**TestSessionTimeout**||사용자가 지정된 시간 제한을 초과하는 테스트 세션을 종료할 수 있도록 합니다. 시간 제한을 설정하면 리소스가 효율적으로 사용되고 테스트 세션이 설정된 시간으로 제한됩니다. 이 설정은 **Visual Studio 2017 버전 15.5** 이상에서 사용할 수 있습니다.|
|**DotnetHostPath**||testhost를 실행하는 데 사용되는 dotnet 호스트의 사용자 지정 경로를 지정합니다. dotnet/runtime 리포지토리를 빌드하는 경우와 같이 사용자 자체 dotnet을 빌드할 때 유용합니다. 이 옵션을 지정하면 testhost.exe 찾기를 건너뛰고 항상 testhost.dll을 사용합니다. 

## <a name="datacollectors-element-diagnostic-data-adapters"></a>DataCollectors 요소(진단 데이터 어댑터)

**DataCollectors** 요소는 진단 데이터 어댑터의 설정을 지정합니다. 진단 데이터 어댑터는 테스트 환경 및 애플리케이션에 대한 추가 정보를 수집합니다. 각 어댑터에는 기본 설정이 있으며 기본 설정을 사용하지 않으려는 경우에만 설정을 제공해야 합니다.

```xml
<DataCollectionRunSettings>
  <DataCollectors>
    <!-- data collectors -->
  </DataCollectors>
</DataCollectionRunSettings>
```

### <a name="codecoverage-data-collector"></a>CodeCoverage 데이터 수집기

코드 검사 데이터 수집기는 테스트에서 애플리케이션 코드 중 실행된 부분에 대한 로그를 만듭니다. 코드 검사 설정을 사용자 지정하는 방법에 대한 자세한 내용은 [코드 검사 분석 사용자 지정](../test/customizing-code-coverage-analysis.md)을 참조하세요.

```xml
<DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
  <Configuration>
    <CodeCoverage>
      <ModulePaths>
        <Exclude>
          <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
        </Exclude>
      </ModulePaths>

      <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
      <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
      <CollectFromChildProcesses>True</CollectFromChildProcesses>
      <CollectAspDotNet>False</CollectAspDotNet>
    </CodeCoverage>
  </CodeCoverage>
</Configuration>
```

### <a name="videorecorder-data-collector"></a>VideoRecorder 데이터 수집기

비디오 데이터 수집기는 테스트를 실행할 때 기록되는 화면을 캡처합니다. 이 기록은 UI 테스트 문제 해결에 유용합니다. 비디오 데이터 수집기는 **Visual Studio 2017 버전 15.5** 이상에서 제공됩니다. 이 데이터 수집기를 구성하는 방법의 예제는 [예제 *.runsettings 파일](#example-runsettings-file)을 참조하세요.

다른 형식의 진단 데이터 어댑터를 사용자 지정하려면 [테스트 설정 파일](../test/collect-diagnostic-information-using-test-settings.md)을 사용합니다.

### <a name="blame-data-collector"></a>원인 데이터 수집기

이 옵션을 사용하여 테스트 호스트 크래시가 발생하는 문제가 있는 테스트를 격리할 수 있습니다. 수집기를 실행하면 크래시가 발생하기 전에 테스트 실행 순서를 캡처하는 *TestResults*의 출력 파일(*Sequence.xml*)이 만들어집니다. 

```xml
<DataCollector friendlyName="blame" enabled="True">
</DataCollector>
```

## <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="docsUrl" value="https://docs.microsoft.com" />
</TestRunParameters>
```

테스트 실행 매개 변수를 사용하면 런타임에 테스트에 제공되는 변수와 값을 정의할 수 있습니다. MSTest <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType> 속성(또는 NUnit [TestContext](https://docs.nunit.org/articles/nunit/writing-tests/TestContext.html))을 사용하여 매개 변수에 액세스합니다.

```csharp
private string _appUrl;
public TestContext TestContext { get; set; }

[TestMethod] // [Test] for NUnit
public void HomePageTest()
{
    string _appURL = TestContext.Properties["webAppUrl"];
}
```

테스트 실행 매개 변수를 사용하려면 공용 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> 속성을 테스트 클래스에 추가합니다.

## <a name="loggerrunsettings-element"></a>LoggerRunSettings 요소

`LoggerRunSettings` 섹션은 테스트 실행에 사용할 로거를 하나 이상 정의합니다. 가장 일반적인 로거는 콘솔, Visual Studio 테스트 결과 파일(trx), html입니다.

```xml
<LoggerRunSettings>
    <Loggers>        
      <Logger friendlyName="console" enabled="True">
        <Configuration>
            <Verbosity>quiet</Verbosity>
        </Configuration>
      </Logger>
      <Logger friendlyName="trx" enabled="True">
        <Configuration>
          <LogFileName>foo.trx</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="html" enabled="True">
        <Configuration>
          <LogFileName>foo.html</LogFileName>
        </Configuration>
      </Logger>
    </Loggers>
  </LoggerRunSettings>
```

## <a name="mstest-element"></a>MSTest 요소

이러한 설정은 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 특성을 가진 테스트 메서드를 실행하는 테스트 어댑터에 따라 달라집니다.

```xml
<MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
</MSTest>
```

|구성|기본값|값|
|-|-|-|
|**ForcedLegacyMode**|false|Visual Studio 2012에서 MSTest 어댑터는 더욱 빠르고 확장성 가능하도록 최적화되었습니다. 테스트가 실행되는 순서와 같은 일부 동작은 이전 버전 Visual Studio처럼 정확하지 않을 수 있습니다. 이전 테스트 어댑터를 사용하려면 이 값을 **true**로 설정합니다.<br /><br />예를 들어, 단위 테스트에 대해 *app.config* 파일을 지정한 경우 이 설정을 사용할 수 있습니다.<br /><br />새 어댑터를 사용할 수 있도록 테스트를 리팩터링하는 것이 좋습니다.|
|**IgnoreTestImpact**|false|테스트 영향 기능은 MSTest 또는 Microsoft Test Manager(Visual Studio 2017에서 더 이상 사용되지 않음)에서 실행할 때 최근 변경 내용의 영향을 받는 테스트의 우선 순위를 지정합니다. 이 설정에서는 이 기능이 비활성화됩니다. 자세한 내용은 [이전 빌드 이후 실행해야 할 테스트](https://msdn.microsoft.com/library/dd286589)를 참조하세요.|
|**SettingsFile**||여기에서 MSTest 어댑터와 함께 사용할 테스트 설정 파일을 지정할 수 있습니다. [설정 메뉴에서](#specify-a-run-settings-file-in-the-ide) 테스트 설정 파일을 지정할 수도 있습니다.<br /><br />이 값을 지정하면 **ForcedlegacyMode** 도 **true**로 설정해야 합니다.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|false|테스트 실행이 완료되면 MSTest가 종료됩니다. 테스트의 일부로 시작된 프로세스도 종료됩니다. 테스트 실행기를 활성 상태로 유지하려면 값을 **true**로 설정합니다. 예를 들어, 이 설정을 사용하여 브라우저가 코딩된 UI 테스트 사이에서 계속 실행되도록 할 수 있습니다.|
|**DeploymentEnabled**|true|값을 **false**로 설정할 경우 테스트 메서드에서 지정한 배포 항목이 배포 디렉터리로 복사되지 않습니다.|
|**CaptureTraceOutput**|true|<xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType>을 사용하여 테스트 메서드에서 디버그 추적으로 쓸 수 있습니다.|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|테스트를 실행한 후 배포 디렉터리를 유지하려면 이 값을 **false**로 설정합니다.|
|**MapInconclusiveToFailed**|false|테스트가 불충분한 상태로 완료되는 경우 **테스트 탐색기**에서 건너뛴 상태로 매핑됩니다. 결과가 불충분한 테스트를 실패로 표시하려는 경우 값을 **true**로 설정합니다.|
|**InProcMode**|false|테스트를 MSTest 어댑터와 동일한 프로세스에서 실행하려면 이 값을 **true**로 설정합니다. 이 설정을 사용하면 성능이 약간 향상됩니다. 하지만 테스트가 종료될 때 예외가 발생하면 다른 테스트를 계속할 수 없습니다.|
|**AssemblyResolution**|false|단위 테스트를 찾아서 실행하는 경우 추가 어셈블리에 대한 경로를 지정할 수 있습니다. 예를 들어 테스트 어셈블리와 동일한 디렉터리에 존재하지 않는 종속성 어셈블리에 대해 이러한 경로를 사용합니다. 경로를 지정하려면 **디렉터리 경로** 요소를 사용합니다. 경로는 환경 변수를 포함할 수 있습니다.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="example-runsettings-file"></a>예제 *.runsettings* 파일

다음 XML에는 일반적인 *.runsettings* 파일의 콘텐츠를 보여 줍니다. 이 코드를 복사하고 필요에 따라 편집합니다.

값에는 기본값이 있으므로 파일의 각 요소는 선택 사항입니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to directory that contains .runsettings file-->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- x86 or x64 -->
    <!-- You can also change it from the Test menu; choose "Processor Architecture for AnyCPU Projects" -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>

    <!-- TestSessionTimeout was introduced in Visual Studio 2017 version 15.5 -->
    <!-- Specify timeout in milliseconds. A valid value should be greater than 0 -->
    <TestSessionTimeout>10000</TestSessionTimeout>
  </RunConfiguration>

  <!-- Configurations for data collectors -->
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
            <ModulePaths>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>

      <DataCollector uri="datacollector://microsoft/VideoRecorder/1.0" assemblyQualifiedName="Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder.VideoRecorderDataCollector, Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" friendlyName="Screen and Voice Recorder">
        <!--Video data collector was introduced in Visual Studio 2017 version 15.5 -->
        <Configuration>
          <!-- Set "sendRecordedMediaForPassedTestCase" to "false" to add video attachments to failed tests only -->
          <MediaRecorder sendRecordedMediaForPassedTestCase="true"  xmlns="">           
            <ScreenCaptureVideo bitRate="512" frameRate="2" quality="20" />
          </MediaRecorder>
        </Configuration>
      </DataCollector>

      <!-- Configuration for blame data collector -->
      <DataCollector friendlyName="blame" enabled="True">
      </DataCollector>

    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at run time -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>
  
  <!-- Configuration for loggers -->
  <LoggerRunSettings>
    <Loggers>      
      <Logger friendlyName="console" enabled="True">
        <Configuration>
            <Verbosity>quiet</Verbosity>
        </Configuration>
      </Logger>
      <Logger friendlyName="trx" enabled="True">
        <Configuration>
          <LogFileName>foo.trx</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="html" enabled="True">
        <Configuration>
          <LogFileName>foo.html</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="blame" enabled="True" />
    </Loggers>
  </LoggerRunSettings>

  <!-- Adapter Specific sections -->

  <!-- MSTest adapter -->
  <MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
  </MSTest>

</RunSettings>
```

## <a name="specify-environment-variables-in-the-runsettings-file"></a>*.runsettings* 파일에서 환경 변수를 지정합니다.

환경 변수는 테스트 호스트와 직접 상호 작용할 수 있는 *.runsettings* 파일에서 설정할 수 있습니다. *DOTNET_ROOT* 같은 환경 변수를 설정해야 하는 중요한 프로젝트를 지원하려면 *.runsettings* 파일에 환경 변수를 지정해야 합니다. 해당 변수는 테스트 호스트 프로세스를 생성하는 동안 설정되며 호스트에서 사용할 수 있습니다.

### <a name="example"></a>예제

다음 코드는 환경 변수를 전달하는 샘플 *.runsettings* 파일입니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <RunConfiguration>
    <EnvironmentVariables>
      <!-- List of environment variables we want to set-->
      <DOTNET_ROOT>C:\ProgramFiles\dotnet</DOTNET_ROOT>
      <SDK_PATH>C:\Codebase\Sdk</SDK_PATH>
    </EnvironmentVariables>
  </RunConfiguration>
</RunSettings>
```

**RunConfiguration** 노드에는 **EnvironmentVariables** 노드가 포함되어야 합니다. 환경 변수는 요소 이름 및 해당 값으로 지정할 수 있습니다.

> [!NOTE]
> 테스트 호스트를 시작할 때 항상 해당 환경 변수를 설정해야 하므로 테스트를 항상 별도의 프로세스로 실행해야 합니다. 이를 위해 테스트 호스트가 항상 호출되도록 하는 환경 변수가 있는 경우 */InIsolation* 플래그가 지정됩니다.

## <a name="see-also"></a>참조

- [테스트 실행 구성](https://github.com/microsoft/vstest-docs/blob/master/docs/configure.md)
- [코드 검사 분석 사용자 지정](../test/customizing-code-coverage-analysis.md)
- [Visual Studio 테스트 작업(Azure Test Plans)](/azure/devops/pipelines/tasks/test/vstest?view=vsts)


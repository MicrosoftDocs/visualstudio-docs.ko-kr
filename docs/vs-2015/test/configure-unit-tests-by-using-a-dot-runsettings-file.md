---
title: .runsettings 파일을 사용하여 단위 테스트 구성 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: f7e9e4a2-5d01-4f78-b408-5be3892bd162
caps.latest.revision: 28
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b9779dd685ad662cd0761dc85be58d0dbb3ccf0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660663"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>.runsettings 파일을 사용하여 단위 테스트 구성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*.runsettings 파일을 사용하여 Visual Studio의 단위 테스트를 구성할 수 있습니다. 확장명으로 ‘.runsettings’를 사용하면 파일 이름은 아무런 상관이 없습니다. 예를 들어, 테스트가 실행되는 .NET Framework, 테스트 결과가 전달되는 디렉터리 및 테스트 실행 중에 수집된 데이터를 변경할 수 있습니다.

 특수 구성을 원하지 않는다면 *.runsettings 파일이 필요하지 않습니다. 가장 자주 사용하는 경우는 [코드 검사](../test/customizing-code-coverage-analysis.md)를 사용자 지정하는 경우입니다.

> [!NOTE]
> **.runsettings 및 .testsettings**
>
> 테스트 구성에는 두 가지 파일 형식이 필요합니다. *.runsettings는 단위 테스트에 사용됩니다. \*.testsettings는 [랩 환경 테스트](https://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901), 웹 성능 및 로드 테스트 그리고 IntelliTrace 및 이벤트 로그 어댑터와 같은 진단 데이터 어댑터의 일부 유형을 사용자 지정하는 데 사용됩니다.
>
> Visual Studio 2010까지 Visual Studio의 이전 버전에서는 *.testsettings 파일을 사용해서 단위 테스트를 사용자 지정할 수 있었습니다. 여전히 *.testsettings 파일을 사용해서 단위 테스트를 사용자 지정할 수도 있지만 \*.runsettings 파일에서 동일한 구성을 사용하는 것보다 테스트가 훨씬 느리게 실행됩니다.

## <a name="customizing-tests-with-a-runsettings-file"></a>.runsettings 파일을 사용하여 테스트 사용자 지정

1. XML 파일을 Visual Studio 솔루션에 추가하고 이름을 test.runsettings로 바꿉니다. 파일 이름은 아무런 상관이 없지만 확장명은 .runsettings를 사용해야 합니다.

2. 파일 콘텐츠를 [예제](#example)로 바꿉니다.

    각자의 요구에 따라 편집합니다.

3. **테스트** 메뉴에서 **테스트 설정**, **테스트 설정 파일 선택**을 차례로 선택합니다.

   솔루션에 \*.runsettings 파일을 두 개 이상 만들고 **테스트 설정** 메뉴를 사용하여 다른 시간에 사용하거나 사용하지 않도록 설정할 수 있습니다.

   ![실행 설정 파일 사용](../test/media/runsettings-1.png "RunSettings-1")

## <a name="copy-this-example-runsettings-file"></a><a name="example"></a> 이 예제의 .runsettings 파일 복사
 다음은 일반적인 *.runsettings 파일입니다. 모든 값에는 기본값이 있으므로 파일의 각 요소는 선택 사항입니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to solution directory -->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- [x86] | x64
      - You can also change it from menu Test, Test Settings, Default Processor Architecture -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
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

    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at runtime -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>

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

 .runsettings 파일도 [코드 검사](../test/customizing-code-coverage-analysis.md)를 구성하는 데 사용됩니다.

 이 항목의 나머지 부분은 파일 콘텐츠에 대해 설명합니다.

## <a name="edit-your-runsettings-file"></a>.runsettings 파일을 편집합니다.
 .runsettings 파일에는 다음과 같은 요소가 있습니다.

### <a name="test-run-configuration"></a>테스트 실행 구성

|노드|기본값|값|
|----------|-------------|------------|
|`ResultsDirectory`||테스트 결과가 배치될 디렉터리입니다.|
|`TargetFrameworkVersion`|Framework40|Framework35, Framework40, Framework45<br /><br /> 테스트를 검색하고 실행하는 데 사용할 단위 테스트 프레임워크의 버전을 지정합니다. 이 버전은 단위 테스트 프로젝트의 빌드 속성에 지정하는 .NET 플랫폼의 버전과 다를 수 있습니다.|
|`TargetPlatform`|x86|x86, x64|
|`TreatTestAdapterErrorsAsWarnings`|false|false, true|
|`TestAdaptersPaths`||TestAdapters가 있는 디렉터리에 대한 하나 또는 여러 경로|
|`MaxCpuCount`|1|단위 테스트를 실행하는 경우 시스템에서 사용 가능한 코어를 사용하여 병렬 테스트 실행의 정도를 제어합니다.  테스트 실행 엔진이 사용 가능한 각 코어에서 별도의 프로세스로 시작되며, 실행할 테스트가 있는 컨테이너(예: 어셈블리, DLL 또는 관련 아티팩트)를 각 코어에 제공합니다.  테스트 컨테이너는 예약 단위입니다.  각 컨테이너에서 테스트는 테스트 프레임워크에 따라 실행됩니다.  많은 컨테이너가 있는 경우 프로세스가 컨테이너 내의 테스트 실행을 마치면 사용 가능한 다음 컨테이너가 제공됩니다.<br /><br /> MaxCpuCount는 다음과 같을 수 있습니다.<br /><br /> n, 여기서 1 < = n < = 코어 수에 해당하며 최대 n개의 프로세스가 시작됩니다.<br /><br /> n, 여기서 n = 다른 모든 값이 되며, 시작되는 프로세스의 수는 컴퓨터에서 사용 가능한 코어 수까지입니다.|

### <a name="diagnostic-data-adapters-data-collectors"></a>진단 데이터 어댑터(데이터 수집기)
 `DataCollectors` 요소는 진단 데이터 어댑터의 설정을 지정합니다. 진단 데이터 어댑터는 테스트 환경 및 애플리케이션에 대한 추가 정보를 수집하는 데 사용합니다. 각 어댑터에는 기본 설정이 있으며 기본 설정을 사용하지 않으려는 경우에만 설정을 제공해야 합니다.

#### <a name="code-coverage-adapter"></a>코드 검사 어댑터
 코드 검사 데이터 수집기는 테스트에서 애플리케이션 코드 중 실행된 부분에 대한 로그를 만듭니다. 코드 검사의 설정을 사용자 지정하는 방법에 대한 자세한 내용은 [코드 검사 분석 사용자 지정](../test/customizing-code-coverage-analysis.md)을 참조하세요.

#### <a name="other-diagnostic-data-adapters"></a>기타 진단 데이터 어댑터
 코드 검사 어댑터는 현재 실행 설정 파일을 사용하여 사용자 지정할 수 있는 유일한 어댑터입니다.

 다른 종류의 진단 데이터 어댑터를 사용자 지정하려면 테스트 설정 파일을 사용해야 합니다. 자세한 내용은 [Visual Studio 테스트에 대한 테스트 설정 지정](https://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901)을 참조하세요.

#### <a name="testrunparameters"></a>TestRunParameters
 TestRunParameters는 런타임에 테스트에서 사용할 수 있는 변수 및 값을 정의하는 방법을 제공합니다.

### <a name="mstest-run-settings"></a>MSTest 실행 설정
 이러한 설정은 `[TestMethod]` 특성을 가진 테스트 메서드를 실행하는 테스트 어댑터에 따라 달라집니다.

|Configuration|기본값|값|
|-------------------|-------------|------------|
|ForcedLegacyMode|false|Visual Studio 2012에서 MSTest 어댑터는 더욱 빠르고 확장성 가능하도록 최적화되었습니다. 테스트가 실행되는 순서와 같은 일부 동작은 이전 버전 Visual Studio처럼 정확하지 않을 수 있습니다. 이전 테스트 어댑터를 사용하려면 이 값을 `true` 로 설정합니다.<br /><br /> 예를 들어, 단위 테스트에 대해 app.config 파일을 지정한 경우 이전 테스트 어댑터를 사용할 수 있습니다.<br /><br /> 새 어댑터를 사용할 수 있도록 테스트를 리팩터링하는 것이 좋습니다.|
|IgnoreTestImpact|false|테스트 영향 기능은 MSTest 또는 Microsoft Test Manager에서 실행할 때 최근 변경 내용의 영향을 받는 테스트의 우선 순위를 지정합니다. 이 설정에서는 이 기능이 비활성화됩니다. 자세한 내용은 [방법: 코드 변경 후 실행할 테스트를 확인하기 위해 데이터 수집](https://msdn.microsoft.com/library/2f921ea1-9bb0-4870-a30f-0521fc22cb47)을 참조하세요.|
|SettingsFile||여기에서 MS 테스트 어댑터와 함께 사용할 테스트 설정 파일을 지정할 수 있습니다. **테스트**, **테스트 설정**, **테스트 설정 파일 선택**메뉴를 사용하여 테스트 설정 파일을 지정할 수도 있습니다.<br /><br /> 이 값을 지정하면 **ForcedlegacyMode** 도 **true**로 설정해야 합니다.<br /><br /> `<RunSettings>   <MSTest>     <SettingsFile>my.testsettings</SettingsFile>      <ForcedLegacyMode>true</ForcedLegacyMode>    </MSTest> </RunSettings>`|
|KeepExecutorAliveAfterLegacyRun|false|테스트 실행이 완료되면 MSTest가 종료됩니다. 테스트에 포함되어 시작된 프로세스도 이때 종료됩니다. 테스트 Executor를 활성 상태로 유지하려면 이 구성을 true로 전환합니다.<br /><br /> 예를 들어, 이 구성을 사용하여 브라우저가 코딩된 UI 테스트 사이에서 계속 실행되도록 할 수 있습니다.|
|DeploymentEnabled|true|이 값을 false로 설정할 경우 테스트 메서드에서 지정한 배포 항목이 배포 디렉터리로 복사되지 않습니다.|
|CaptureTraceOutput|true|Trace.WriteLine을 사용하여 테스트 메서드에서 디버그 추적으로 쓸 수 있습니다. 이 구성을 사용하여 이러한 디버그 추적을 해제할 수 있습니다.|
|DeleteDeploymentDirectoryAfterTestRunIsComplete|true|이 값을 false로 설정하여 테스트를 실행한 후 배포 디렉터리를 유지할 수 있습니다.|
|MapInconclusiveToFailed|false|테스트가 불충분한 상태로 반환되는 경우 일반적으로 테스트 탐색기에서 생략된 상태로 매핑됩니다. 결과가 불충분한 테스트를 실패로 표시하려는 경우 이 구성을 사용합니다.|
|InProcMode|false|테스트를 MS 테스트 어댑터와 동일한 프로세스에서 실행하려면 이 값을 true로 설정합니다. 이 설정을 사용하면 성능이 약간 향상됩니다. 하지만 테스트가 종료될 때 예외가 발생하면 다른 테스트를 계속할 수 없습니다.|
|AssemblyResolution|false|단위 테스트를 찾아서 실행하는 경우 추가 어셈블리에 대한 경로를 지정할 수 있습니다.  예를 들어 테스트 어셈블리와 동일한 디렉터리에 존재하지 않는 종속성 어셈블리에 대해 이러한 경로를 사용합니다.  경로를 지정하려면 "디렉터리 경로" 요소를 사용합니다.  경로는 환경 변수를 포함할 수 있습니다.<br /><br /> `<AssemblyResolution>  <Directory Path>"D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>관련 항목
 [코드 검사 분석 사용자 지정](../test/customizing-code-coverage-analysis.md) [Visual Studio 테스트에 대 한 테스트 설정 지정](https://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901)

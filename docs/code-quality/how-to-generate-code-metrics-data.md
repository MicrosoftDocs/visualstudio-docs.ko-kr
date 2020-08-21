---
title: IDE 또는 명령줄에서 코드 메트릭 생성
ms.date: 11/02/2018
ms.topic: how-to
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f85c17321defe08dc96ccc04bc9dea717e3b4183
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88706518"
---
# <a name="how-to-generate-code-metrics-data"></a>방법: 코드 메트릭 데이터 생성

다음 세 가지 방법으로 코드 메트릭 데이터를 생성할 수 있습니다.

- [.Net 코드 품질 분석기](#net-code-quality-analyzers-code-metrics-rules) 를 사용 하도록 설정 하 고 여기에 포함 된 4 개의 코드 메트릭 (유지 관리) 규칙을 사용 하도록 설정 합니다.

- Visual Studio 내에서 [ **분석**  >  **코드 메트릭 계산** ](#calculate-code-metrics-menu-command) 메뉴 명령을 선택 합니다.

- C# 및 Visual Basic 프로젝트에 대한 [명령줄](#command-line-code-metrics)에서

## <a name="net-code-quality-analyzers-code-metrics-rules"></a>.NET 코드 품질 분석기 코드 메트릭 규칙

.NET 코드 품질 분석기에는 다음과 같은 여러 코드 메트릭 [분석기](roslyn-analyzers-overview.md) 규칙이 포함 되어 있습니다.

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502.md)
- [CA1505](ca1505.md)
- [CA1506](ca1506.md)

이러한 규칙은 기본적으로 사용 하지 않도록 설정 되어 있지만 [**솔루션 탐색기**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) 또는 [규칙 집합](using-rule-sets-to-group-code-analysis-rules.md) 파일에서 사용 하도록 설정할 수 있습니다. 예를 들어 규칙 CA1502을 경고로 사용 하도록 설정 하려면. 규칙 집합 파일에 다음 항목이 포함 됩니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Configuration

코드 메트릭 규칙이 발생 하는 임계값을 구성할 수 있습니다.

1. 텍스트 파일을 만듭니다. 예를 들어 *CodeMetricsConfig.txt*이름을 지정할 수 있습니다.

2. 다음 형식으로 텍스트 파일에 원하는 임계값을 추가 합니다.

   ```txt
   CA1502: 10
   ```

   이 예제에서 rule [CA1502](ca1502.md) 는 메서드의 순환 복잡성이 10 보다 클 때 발생 하도록 구성 됩니다.

3. Visual Studio의 **속성** 창 또는 프로젝트 파일에서 구성 파일의 빌드 작업을 [**additionalfiles**](../ide/build-actions.md#build-action-values)로 표시 합니다. 예를 들면 다음과 같습니다.

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>코드 메트릭 계산 메뉴 명령

**분석**  >  **코드 메트릭 계산** 메뉴를 사용 하 여 IDE에서 열려 있는 하나 이상의 프로젝트에 대 한 코드 메트릭을 생성 합니다.

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>전체 솔루션에 대 한 코드 메트릭 결과 생성

다음 방법 중 하나를 통해 전체 솔루션에 대 한 코드 메트릭 결과를 생성할 수 있습니다.

- 메뉴 모음에서 **분석**을 선택 하 여  >  솔루션에 대 한**코드 메트릭 계산**을 선택  >  **For Solution**합니다.

- **솔루션 탐색기**에서 솔루션을 마우스 오른쪽 단추로 클릭 한 다음 **코드 메트릭 계산**을 선택 합니다.

- **코드 메트릭 결과** 창에서 **솔루션에 대 한 코드 메트릭 계산** 단추를 선택 합니다.

결과가 생성 되 고 **코드 메트릭 결과** 창이 표시 됩니다. 결과 세부 정보를 보려면 **계층** 열의 트리를 확장 합니다.

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>하나 이상의 프로젝트에 대 한 코드 메트릭 결과 생성

1. **솔루션 탐색기**에서 하나 이상의 프로젝트를 선택 합니다.

1. 메뉴 모음에서 **분석**  >  **Calculate Code Metrics**  >  **선택한 프로젝트에 대 한**코드 메트릭 계산을 선택 합니다.

결과가 생성 되 고 **코드 메트릭 결과** 창이 표시 됩니다. 결과 세부 정보를 보려면 **계층 구조**에서 트리를 확장 합니다.

::: moniker range="vs-2017"

> [!NOTE]
> **코드 메트릭 계산** 명령은 .net Core 및 .NET Standard 프로젝트에 대해 작동 하지 않습니다. .NET Core 또는 .NET Standard 프로젝트에 대 한 코드 메트릭을 계산 하려면 다음을 수행할 수 있습니다.
>
> - 대신 [명령줄](#command-line-code-metrics) 에서 코드 메트릭을 계산 합니다.
>
> - [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) 로 업그레이드

::: moniker-end

## <a name="command-line-code-metrics"></a>명령줄 코드 메트릭

C #에 대 한 명령줄에서 코드 메트릭 데이터를 생성 하 고 .NET Framework, .NET Core 및 .NET Standard 앱에 대 한 Visual Basic 프로젝트를 생성할 수 있습니다. 명령줄에서 코드 메트릭을 실행 하려면 [Microsoft CodeAnalysis. 메트릭 NuGet 패키지](#microsoftcodeanalysismetrics-nuget-package) 를 설치 하거나 [Metrics.exe](#metricsexe) 실행 파일을 직접 작성 합니다.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Microsoft CodeAnalysis. 메트릭 NuGet 패키지

명령줄에서 코드 메트릭 데이터를 생성 하는 가장 쉬운 방법은 [Microsoft CodeAnalysis. 메트릭](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) NuGet 패키지를 설치 하는 것입니다. 패키지를 설치한 후에는 `msbuild /t:Metrics` 프로젝트 파일이 포함 된 디렉터리에서를 실행 합니다. 예를 들면 다음과 같습니다.

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:29:57 PM.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics\Metrics.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:ClassLibrary3.Metrics.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'ClassLibrary3.Metrics.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

을 지정 하 여 출력 파일 이름을 재정의할 수 있습니다 `/p:MetricsOutputFile=<filename>` . 을 지정 하 여 [레거시 스타일](#previous-versions) 코드 메트릭 데이터를 가져올 수도 있습니다 `/p:LEGACY_CODE_METRICS_MODE=true` . 예를 들면 다음과 같습니다.

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics /p:LEGACY_CODE_METRICS_MODE=true /p:MetricsOutputFile="Legacy.xml"
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:31:00 PM.
The "MetricsOutputFile" property is a global property, and cannot be modified.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics.Legacy\Metrics.Legacy.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:Legacy.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'Legacy.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

### <a name="code-metrics-output"></a>코드 메트릭 출력

생성 된 XML 출력은 다음 형식을 사용 합니다.

::: moniker range=">=vs-2019"

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeMetricsReport Version="1.0">
  <Targets>
    <Target Name="ConsoleApp20.csproj">
      <Assembly Name="ConsoleApp20, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null">
        <Metrics>
          <Metric Name="MaintainabilityIndex" Value="100" />
          <Metric Name="CyclomaticComplexity" Value="1" />
          <Metric Name="ClassCoupling" Value="1" />
          <Metric Name="DepthOfInheritance" Value="1" />
          <Metric Name="SourceLines" Value="11" />
          <Metric Name="ExecutableLines" Value="1" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="SourceLines" Value="11" />
              <Metric Name="ExecutableLines" Value="1" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="SourceLines" Value="7" />
                  <Metric Name="ExecutableLines" Value="1" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="SourceLines" Value="4" />
                      <Metric Name="ExecutableLines" Value="1" />
                    </Metrics>
                  </Method>
                </Members>
              </NamedType>
            </Types>
          </Namespace>
        </Namespaces>
      </Assembly>
    </Target>
  </Targets>
</CodeMetricsReport>
```

::: moniker-end
::: moniker range="vs-2017"

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeMetricsReport Version="1.0">
  <Targets>
    <Target Name="ConsoleApp20.csproj">
      <Assembly Name="ConsoleApp20, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null">
        <Metrics>
          <Metric Name="MaintainabilityIndex" Value="100" />
          <Metric Name="CyclomaticComplexity" Value="1" />
          <Metric Name="ClassCoupling" Value="1" />
          <Metric Name="DepthOfInheritance" Value="1" />
          <Metric Name="LinesOfCode" Value="11" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="LinesOfCode" Value="11" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="LinesOfCode" Value="7" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="LinesOfCode" Value="4" />
                    </Metrics>
                  </Method>
                </Members>
              </NamedType>
            </Types>
          </Namespace>
        </Namespaces>
      </Assembly>
    </Target>
  </Targets>
</CodeMetricsReport>
```

::: moniker-end

### <a name="metricsexe"></a>Metrics.exe

NuGet 패키지를 설치 하지 않으려면 *Metrics.exe* 실행 파일을 직접 생성 하 고 사용할 수 있습니다. *Metrics.exe* 실행 파일을 생성 하려면:

1. [Dotnet/roslyn](https://github.com/dotnet/roslyn-analyzers) 리포지토리를 복제 합니다.
2. 관리자 권한으로 Visual Studio에 대 한 개발자 명령 프롬프트를 엽니다.
3. **Roslyn-분석기** 리포지토리의 루트에서 다음 명령을 실행 합니다.`Restore.cmd`
4. 디렉터리를 *src\Tools*로 변경 합니다.
5. 다음 명령을 실행 하 여 **메트릭의 .csproj** 프로젝트를 빌드합니다.

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   *Metrics.exe* 이름이 지정 된 실행 파일은 리포지토리 루트 아래의 *artifacts\bin* 디렉터리에 생성 됩니다.

#### <a name="metricsexe-usage"></a>Metrics.exe 사용

*Metrics.exe*를 실행 하려면 프로젝트 또는 솔루션과 출력 XML 파일을 인수로 제공 합니다. 예를 들면 다음과 같습니다.

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>레거시 모드

*레거시 모드*에서 *Metrics.exe* 빌드를 선택할 수 있습니다. 도구의 레거시 모드 버전은 [이전 버전의 도구에서 생성](#previous-versions)된 것과 더 가까운 메트릭 값을 생성 합니다. 또한 레거시 모드에서는 이전 버전의 도구에서 코드 메트릭을 생성 한 것과 동일한 메서드 형식 집합에 대 한 코드 메트릭을 생성 *Metrics.exe* 합니다. 예를 들어 필드 및 속성 이니셜라이저의 코드 메트릭 데이터를 생성 하지 않습니다. 레거시 모드는 이전 버전과의 호환성을 위해 또는 코드 메트릭 번호를 기반으로 하는 코드 체크 인 게이트를 사용 하는 경우에 유용 합니다. 레거시 모드에서 *Metrics.exe* 를 빌드하는 명령은 다음과 같습니다.

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

자세한 내용은 [레거시 모드에서 코드 메트릭 생성 사용](https://github.com/dotnet/roslyn-analyzers/pull/1841)을 참조 하세요.

### <a name="previous-versions"></a>이전 버전

::: moniker range=">=vs-2019"
Visual Studio 2015에는 *Metrics.exe*라고도 하는 명령줄 코드 메트릭 도구가 포함 되어 있습니다. 이 이전 버전의 도구는 이진 분석 (즉, 어셈블리 기반 분석)을 수행 했습니다. 최신 버전의 *Metrics.exe* 도구는 소스 코드를 대신 분석 합니다. 최신 *Metrics.exe* 도구는 소스 코드 기반 이므로 명령줄 코드 메트릭 결과는 VISUAL Studio IDE와 이전 버전의 *Metrics.exe*에 의해 생성 된 것과 다를 수 있습니다. Visual Studio 2019부터 Visual Studio IDE는 명령줄 도구와 같은 소스 코드를 분석 하 고 결과는 동일 해야 합니다.

::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2015에는 *Metrics.exe*라고도 하는 명령줄 코드 메트릭 도구가 포함 되어 있습니다. 이 이전 버전의 도구는 이진 분석 (즉, 어셈블리 기반 분석)을 수행 했습니다. 새 *Metrics.exe* 도구는 대신 소스 코드를 분석 합니다. 새 *Metrics.exe* 도구는 소스 코드 기반 이므로 명령줄 코드 메트릭 결과는 VISUAL Studio IDE와 이전 버전의 *Metrics.exe*에 의해 생성 된 것과 다릅니다.
::: moniker-end

새 명령줄 코드 메트릭 도구는 솔루션과 프로젝트를 로드할 수 있는 한 소스 코드 오류가 있는 경우에도 메트릭을 계산 합니다.

#### <a name="metric-value-differences"></a>메트릭 값 차이

::: moniker range=">=vs-2019"
Visual Studio 2019 버전 16.4 및 메트릭 (2.9.5)에서 시작 `SourceLines` 하 `ExecutableLines` 여 이전 `LinesOfCode` 메트릭을 바꿉니다. 새 메트릭에 대 한 설명은 [코드 메트릭 값](../code-quality/code-metrics-values.md)을 참조 하세요. `LinesOfCode`메트릭은 레거시 모드에서 사용할 수 있습니다.
::: moniker-end
::: moniker range="vs-2017"
`LinesOfCode`메트릭은 새 명령줄 코드 메트릭 도구에서 더 정확 하 고 안정적입니다. Codegen 차이가 없으며 도구 집합 또는 런타임이 변경 될 때 변경 되지 않습니다. 새 도구는 빈 줄 및 주석을 포함 하 여 실제 코드 줄 수를 계산 합니다.
::: moniker-end

및와 같은 기타 `CyclomaticComplexity` 메트릭은 `MaintainabilityIndex` 이전 버전의 *Metrics.exe*와 같은 수식을 사용 하지만 새 도구는 `IOperations` IL (중간 언어) 명령 대신 (논리적 원본 명령)의 수를 계산 합니다. Visual Studio IDE와 이전 버전의 *Metrics.exe*에 의해 생성 되는 숫자는 약간 다릅니다.

## <a name="see-also"></a>참고 항목

- [코드 메트릭 결과 창 사용](../code-quality/working-with-code-metrics-data.md)
- [코드 메트릭 값](../code-quality/code-metrics-values.md)

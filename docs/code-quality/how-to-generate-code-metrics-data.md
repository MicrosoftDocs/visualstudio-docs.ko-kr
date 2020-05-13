---
title: IDE 또는 명령줄에서 코드 메트릭 생성
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1abae26ed8a5e5db74f7b0d04db66d9d99930d5c
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649306"
---
# <a name="how-to-generate-code-metrics-data"></a>방법: 코드 메트릭 데이터 생성

다음 세 가지 방법으로 코드 메트릭 데이터를 생성할 수 있습니다.

- [FxCop 분석기를](#fxcop-analyzers-code-metrics-rules) 설치하고 포함된 네 가지 코드 메트릭(유지 관리 가능성) 규칙을 사용하도록 설정합니다.

- Visual Studio 내에서 코드 메트릭 [ **계산** > ](#calculate-code-metrics-menu-command) 메뉴 분석 명령을 선택합니다.

- C# 및 Visual Basic 프로젝트에 대한 [명령줄](#command-line-code-metrics)에서

## <a name="fxcop-analyzers-code-metrics-rules"></a>FxCop 분석기 코드 메트릭 규칙

[FxCop분석기 NuGet 패키지에는](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) 다음과 같은 몇 가지 코드 메트릭 [분석기](roslyn-analyzers-overview.md) 규칙이 포함되어 있습니다.

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502.md)
- [CA1505](ca1505.md)
- [CA1506](ca1506.md)

이러한 규칙은 기본적으로 비활성화되어 있지만 [**솔루션 탐색기**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) 또는 [규칙 집합](using-rule-sets-to-group-code-analysis-rules.md) 파일에서 사용하도록 설정할 수 있습니다. 예를 들어 규칙 CA1502를 경고로 사용하도록 설정하려면 .ruleset 파일에 다음 항목이 포함됩니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>구성

FxCop 분석기 패키지 화재에서 코드 메트릭이 규칙하는 임계값을 구성할 수 있습니다.

1. 텍스트 파일을 만듭니다. 예를 들어 *CodeMetricsConfig.txt*.

2. 다음 형식으로 텍스트 파일에 원하는 임계값을 추가합니다.

   ```txt
   CA1502: 10
   ```

   이 예제에서 [CA1502](ca1502.md) 규칙은 메서드의 순환 복잡성이 10보다 클 때 발생하도록 구성됩니다.

3. Visual Studio의 **속성** 창또는 프로젝트 파일에서 구성 파일의 빌드 작업을 [**AdditionalFiles**](../ide/build-actions.md#build-action-values)로 표시합니다. 다음은 그 예입니다.

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>코드 메트릭 메뉴 명령 계산

코드 계산 메트릭 **분석** > 메뉴를 사용하여 IDE에서 열려 있는 프로젝트 중 하나 또는 모두에 대한 코드**메트릭을 생성합니다.**

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>전체 솔루션에 대한 코드 메트릭 결과 생성

다음 방법 중 에서 전체 솔루션에 대한 코드 메트릭 결과를 생성할 수 있습니다.

- 메뉴 모음에서**솔루션에 대한**코드 메트릭 **계산 분석을** > **선택합니다.** > 

- **솔루션 탐색기에서**솔루션을 마우스 오른쪽 단추로 클릭한 다음 **코드 메트릭 계산을 선택합니다.**

- 코드 **메트릭 결과** 창에서 **솔루션에 대한 코드 메트릭 계산 단추를 선택합니다.**

결과가 생성되고 **코드 메트릭 결과** 창이 표시됩니다. 결과 세부 정보를 보려면 **계층 열에서** 트리를 확장합니다.

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>하나 이상의 프로젝트에 대한 코드 메트릭 결과 생성

1. **솔루션 탐색기에서**하나 이상의 프로젝트를 선택합니다.

1. 메뉴 모음에서**선택한 프로젝트에 대한**코드 메트릭 >  **계산을** > **Calculate Code Metrics**선택합니다.

결과가 생성되고 **코드 메트릭 결과** 창이 표시됩니다. 결과 세부 정보를 보려면 **계층 구조에서**트리를 확장합니다.

::: moniker range="vs-2017"

> [!NOTE]
> .NET 코어 및 .NET 표준 **프로젝트에서는 코드 메트릭 계산** 명령이 작동하지 않습니다. .NET Core 또는 .NET 표준 프로젝트에 대한 코드 메트릭을 계산하려면 다음을 수행할 수 있습니다.
>
> - 대신 [명령줄에서](#command-line-code-metrics) 코드 메트릭 계산
>
> - 비주얼 [스튜디오 2019로](https://visualstudio.microsoft.com/downloads) 업그레이드

::: moniker-end

## <a name="command-line-code-metrics"></a>명령줄 코드 메트릭

.NET Framework, .NET Core 및 .NET 표준 앱에 대한 C# 및 Visual Basic 프로젝트의 명령줄에서 코드 메트릭 데이터를 생성할 수 있습니다. 명령줄에서 코드 메트릭을 실행하려면 [Microsoft.CodeAnalysis.Metrics NuGet 패키지를](#microsoftcodeanalysismetrics-nuget-package) 설치하거나 [Metrics.exe](#metricsexe) 실행 암호를 직접 빌드합니다.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>마이크로소프트.코드분석.메트릭스 NuGet 패키지

명령줄에서 코드 메트릭 데이터를 생성하는 가장 쉬운 방법은 [Microsoft.CodeAnalysis.Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) NuGet 패키지를 설치하는 것입니다. 패키지를 설치한 후 프로젝트 `msbuild /t:Metrics` 파일이 포함된 디렉터리에서 실행합니다. 다음은 그 예입니다.

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

을 지정하여 출력 파일 이름을 `/p:MetricsOutputFile=<filename>`재정의할 수 있습니다. 을 지정하여 [legacy-style](#previous-versions) `/p:LEGACY_CODE_METRICS_MODE=true`레거시 스타일 코드 메트릭 데이터를 얻을 수도 있습니다. 다음은 그 예입니다.

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

생성된 XML 출력은 다음과 같은 형식을 취합니다.

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

### <a name="metricsexe"></a>메트릭스.exe

NuGet 패키지를 설치하지 않으려면 *Metrics.exe* 실행 프로그램을 직접 생성하고 사용할 수 있습니다. *Metrics.exe* 실행 을 생성하려면 다음을 수행하십시오.

1. [도트넷/로슬린 분석기](https://github.com/dotnet/roslyn-analyzers) 리포지토리를 복제합니다.
2. 관리자로서 Visual Studio에 대한 개발자 명령 프롬프트를 엽니다.
3. **roslyn 분석기** 리포지토리의 루트에서 다음 명령을 실행합니다.`Restore.cmd`
4. 디렉터리를 *src\Tools로*변경합니다.
5. 다음 명령을 실행하여 **Metrics.csproj 프로젝트를 빌드합니다.**

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   *Metrics.exe라는* 실행 가능한 실행 항목은 리포지토리 루트 아래의 *아티팩트\bin* 디렉토리에서 생성됩니다.

#### <a name="metricsexe-usage"></a>메트릭스.exe 사용

*Metrics.exe를*실행하려면 프로젝트 또는 솔루션과 출력 XML 파일을 인수로 제공합니다. 다음은 그 예입니다.

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>레거시 모드

레거시 모드에서 *Metrics.exe를* 빌드하도록 선택할 수 *있습니다.* 도구의 레거시 모드 버전은 [이전 버전의 도구가 생성한](#previous-versions)항목에 더 가까운 메트릭 값을 생성합니다. 또한 레거시 모드에서 *Metrics.exe는* 이전 버전의 도구가 코드 메트릭을 생성한 것과 동일한 메서드 유형 집합에 대한 코드 메트릭을 생성합니다. 예를 들어 필드 및 속성 초기화자에 대한 코드 메트릭 데이터를 생성하지 않습니다. 레거시 모드는 이전 버전과의 호환성또는 코드 메트릭 번호를 기반으로 하는 코드 체크인 게이트가 있는 경우에 유용합니다. 레거시 모드에서 *Metrics.exe를* 빌드하는 명령은 다음과 같은 것입니다.

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

자세한 내용은 [레거시 모드에서 코드 메트릭 생성 을 활성화를](https://github.com/dotnet/roslyn-analyzers/pull/1841)참조하십시오.

### <a name="previous-versions"></a>이전 버전

::: moniker range=">=vs-2019"
Visual Studio 2015에는 *Metrics.exe라고도*하는 명령줄 코드 메트릭 도구가 포함되어 있습니다. 이 이전 버전의 도구는 이진 분석, 즉 어셈블리 기반 분석을 했습니다. *Metrics.exe* 도구의 최신 버전은 대신 소스 코드를 분석합니다. 최신 *Metrics.exe* 도구는 소스 코드 기반이므로 명령줄 코드 메트릭 결과는 Visual Studio IDE 및 이전 버전의 *Metrics.exe*에서 생성된 결과와 다를 수 있습니다. Visual Studio 2019에서 시작하여 Visual Studio IDE는 명령줄 도구와 같은 소스 코드를 분석하며 결과는 동일해야 합니다.

::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2015에는 *Metrics.exe라고도*하는 명령줄 코드 메트릭 도구가 포함되어 있습니다. 이 이전 버전의 도구는 이진 분석, 즉 어셈블리 기반 분석을 했습니다. 새 *Metrics.exe* 도구대신 소스 코드를 분석합니다. 새 *Metrics.exe* 도구는 소스 코드 기반이므로 명령줄 코드 메트릭 결과는 Visual Studio IDE 및 이전 버전의 *Metrics.exe*에서 생성된 결과와 다릅니다.
::: moniker-end

새로운 명령줄 코드 메트릭 도구는 솔루션 및 프로젝트를 로드할 수 있는 한 소스 코드 오류가 있는 경우에도 메트릭을 계산합니다.

#### <a name="metric-value-differences"></a>메트릭 값 차이

::: moniker range=">=vs-2019"
Visual Studio 2019 버전 16.4 및 Microsoft.CodeAnalysis.Metics(2.9.5)에서 `SourceLines` 시작하여 이전 `ExecutableLines` `LinesOfCode` 메트릭을 대체합니다. 새 메트릭에 대한 설명은 [코드 메트릭 값을](../code-quality/code-metrics-values.md)참조하십시오. 메트릭은 `LinesOfCode` 레거시 모드에서 사용할 수 있습니다.
::: moniker-end
::: moniker range="vs-2017"
이 `LinesOfCode` 메트릭은 새 명령줄 코드 메트릭 도구에서 보다 정확하고 신뢰할 수 있습니다. 코드겐 의 차이와 는 독립적이며 도구 집합 또는 런타임이 변경될 때 변경되지 않습니다. 새 도구는 빈 줄과 주석을 포함하여 실제 코드 줄을 계산합니다.
::: moniker-end

같은 다른 메트릭 `CyclomaticComplexity` `MaintainabilityIndex` 및 *Metrics.exe의*이전 버전과 동일한 수식을 사용 하지만 `IOperations` 새 도구는 중간 언어 (IL) 지침 대신 (논리 소스 지침)의 수를 계산 합니다. 숫자는 Visual Studio IDE 및 이전 버전의 *Metrics.exe에서*생성된 숫자와 약간 다릅니다.

## <a name="see-also"></a>참고 항목

- [코드 메트릭 결과 창 사용](../code-quality/working-with-code-metrics-data.md)
- [코드 메트릭 값](../code-quality/code-metrics-values.md)

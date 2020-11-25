---
title: FxCop 코드 분석 (이진 분석) 및 .NET 분석기 (소스 분석)
ms.date: 09/06/2018
description: Visual Studio에서 레거시 FxCop (이진 분석) 및 .NET 분석기 (소스 분석)의 차이점을 이해 합니다. 이러한 분석기를 사용 하는 방법에 대 한 질문에 대 한 대답을 참조 하세요.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d581ef60ebfe9ff5aeceae4c16ee4294eae5d850
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112179"
---
# <a name="frequently-asked-questions-about-legacy-fxcop-and-net-analyzers"></a>레거시 FxCop 및 .NET 분석기에 대 한 질문과 대답

레거시 FxCop (이진 분석) 및 .NET 분석기 (원본 분석) 간의 차이점을 이해 하는 것은 약간 복잡할 수 있습니다. 이 문서에서는 사용자가 가질 수 있는 일부 질문을 해결하려고 합니다.

## <a name="whats-the-difference-between-legacy-fxcop-and-net-analyzers"></a>레거시 FxCop와 .NET 분석기 간의 차이점은 무엇 인가요?

레거시 FxCop는 컴파일된 어셈블리에서 빌드 후 분석을 실행합니다. **FxCopCmd.exe** 라는 별도 실행 파일로 실행됩니다. FxCopCmd.exe는 컴파일된 어셈블리를 로드하고, 코드 분석을 실행한 다음, 결과(또는 *진단*)를 보고합니다.

.NET 분석기는 .NET Compiler Platform ("Roslyn")를 기반으로 합니다. [.NET SDK에서 사용 하도록 설정 하거나](install-net-analyzers.md) 프로젝트 또는 솔루션에서 참조 하는 NuGet 패키지로 설치 합니다. 분석기는 컴파일러를 실행 하는 동안 소스 코드 기반 분석을 실행 합니다. 분석기는 **csc.exe** 또는 **vbc.exe** 컴파일러 프로세스 내에서 호스팅되며 프로젝트가 빌드될 때 분석을 실행 합니다. 분석기 결과는 컴파일러 결과와 함께 보고됩니다.

## <a name="whats-the-difference-between-fxcop-analyzers-and-net-analyzers"></a>FxCop 분석기와 .NET 분석기 간의 차이점은 무엇 인가요?

FxCop 분석기와 .NET 분석기는 모두 FxCop CA 규칙의 .NET Compiler Platform ("Roslyn") 분석기 구현을 나타냅니다. Visual Studio 2019 16.8 및 .NET 5.0 이전에 이러한 분석기는 `Microsoft.CodeAnalysis.FxCopAnalyzers` [NuGet 패키지로](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)제공 됩니다. Visual Studio 2019 16.8 및 .NET 5.0부터 이러한 분석기는 [.NET SDK에 포함](/dotnet/fundamentals/code-analysis/overview)되어 있습니다. `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet 패키지로](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)도 사용할 수 있습니다. [FxCop 분석기에서 .net 분석기로의 마이그레이션을](migrate-from-fxcop-analyzers-to-net-analyzers.md)고려 하세요.

## <a name="does-the-run-code-analysis-command-run-net-analyzers"></a>코드 분석 실행 명령이 .NET 분석기를 실행 하나요?

Visual Studio 2019 16.5 릴리스 이전에는 **분석**  >  **실행 코드 분석** 을 선택 하면 레거시 분석이 실행 됩니다. Visual Studio 2019 16.5를 시작 하면 **코드 분석 실행** 메뉴 옵션이 선택한 프로젝트 또는 솔루션에 대 한 Roslyn 기반 분석기를 실행 합니다. .NET 분석기를 설치한 경우에도 실행 됩니다. 자세한 내용은 [방법: 관리 코드에 대해 수동으로 코드 분석 실행](how-to-run-code-analysis-manually-for-managed-code.md)을 참조 하세요.

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>RunCodeAnalysis msbuild 프로젝트 속성은 분석기를 실행하나요?

아니요. 프로젝트 파일에서 **RunCodeAnalysis** 속성(예: *.csproj*)은 레거시 FxCop 실행에만 사용됩니다. **FxCopCmd.exe** 를 호출하는 빌드 후 msbuild 작업을 실행합니다.

## <a name="so-how-do-i-run-net-analyzers-then"></a>그렇다면 .NET 분석기를 어떻게 실행 하나요?

.NET 분석기를 실행 하려면 먼저 [.NET SDK에서 사용 하도록 설정 하거나 NuGet 패키지로 설치](install-net-analyzers.md)합니다. 그런 다음, Visual Studio에서 또는 msbuild를 사용하여 프로젝트 또는 솔루션을 빌드합니다. Roslyn 분석기가 생성 하는 경고 및 오류는 **오류 목록** 또는 명령 창에 표시 됩니다.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-net-analyzers-nuget-package"></a>.NET 분석기 NuGet 패키지를 설치한 후에도 경고 CA0507

.NET 분석기를 설치 했지만 경고가 계속 표시 되는 경우 **"" 코드 분석 실행 "은 빌드 중에 실행 되는 FxCop 분석기를 위해 더 이상 사용 되지 않으므로** [프로젝트 파일](../ide/solutions-and-projects-in-visual-studio.md#project-file) 의 **runcodeanalysis** msbuild 속성을 **false** 로 설정 해야 할 수 있습니다. 그렇지 않으면 각 빌드 후에 레거시 분석이 실행 됩니다.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-net-analyzers"></a>.NET 분석기로 이식 된 규칙은 무엇 인가요?

.NET 분석기로 이식 된 레거시 분석 규칙에 대 한 자세한 내용은 [Fxcop 규칙 포트 상태](fxcop-rule-port-status.md)를 참조 하세요.

## <a name="code-analysis-warnings-are-treated-as-errors"></a>코드 분석 경고는 오류로 처리 됩니다.

프로젝트에서 빌드 옵션을 사용 하 여 경고를 오류로 처리 하는 경우 분석기 경고가 오류로 나타날 수 있습니다. 코드 분석 경고가 오류로 처리 되지 않도록 하려면 [코드 분석 FAQ](../code-quality/analyzers-faq.md#treat-warnings-as-errors)의 단계를 따르세요.

## <a name="see-also"></a>참고 항목

- [.NET Compiler Platform 분석기 개요](roslyn-analyzers-overview.md)
- [.NET 분석기로 마이그레이션](migrate-from-legacy-analysis-to-net-analyzers.md)
- [.NET 분석기 설치](install-net-analyzers.md)

---
title: Roslyn 분석기를 사용한 코드 분석
ms.date: 09/01/2020
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d0489950b9132a36aef8ecb3d8374c02d1a1aee2
ms.sourcegitcommit: d77da260d79471ab139973c51d65b04e0f80fe2e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90560738"
---
# <a name="overview-of-source-code-analysis"></a>소스 코드 분석 개요

.NET Compiler Platform(Roslyn) 분석기는 C# 또는 Visual Basic 코드에서 스타일, 품질, 유지 관리, 디자인 및 기타 문제를 검사합니다. 이 검사 또는 분석은 모든 열려 있는 파일에서 디자인 타임에 수행됩니다. 

분석기는 다음 그룹으로 나눌 수 있습니다.

- [코드 스타일](/visualstudio/ide/editorconfig-code-style-settings-reference?view=vs-2019#convention-categories) 분석기는 Visual Studio에 기본 제공됩니다. 이러한 분석기에 대한 진단 ID 또는 코드는 IDExxxx 형식(예: IDE0067)입니다. 기본 설정은 [텍스트 편집기 옵션 페이지](../ide/code-styles-and-code-cleanup.md) 또는 [EditorConfig 파일](../ide/editorconfig-code-style-settings-reference.md)에서 구성할 수 있습니다. .NET 5.0부터 코드 스타일 분석기는 .NET SDK에 포함되며 빌드 경고 또는 오류로 엄격하게 적용될 수 있습니다. 자세한 내용은 [여기](/dotnet/fundamentals/productivity/code-analysis#code-style-analysis)를 참조하세요.

- [코드 품질](code-analysis-warnings-for-managed-code-by-checkid.md) 분석기는 이제 .NET 5 SDK에 포함되고 기본적으로 사용하도록 설정되어 있습니다. 이러한 분석기에 대한 진단 ID 또는 코드는 CAxxxx 형식(예: CA1822)입니다. 자세한 내용은 [.NET 코드 품질 분석 개요](/dotnet/fundamentals/productivity/code-analysis#code-quality-analysis)를 참조하세요.

- 타사 분석기는 NuGet 패키지 또는 Visual Studio 확장으로 설치할 수 있습니다. [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/), [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)와 같은 타사 분석기.

## <a name="severity-levels-of-analyzers"></a>분석기의 심각도 수준

각 분석기는 다음과 같은 심각도 수준 중 하나를 갖습니다.

| 심각도(솔루션 탐색기) | 심각도(EditorConfig 파일) | 빌드 시간 동작 | 편집기 동작 |
|-|-|-|
| 오류 | `error` | 위반은 오류 목록 및 명령줄 빌드 출력에 오류로 표시되고 빌드가 실패합니다.| 위반 코드는 빨간색 물결선이 밑줄로 표시되고 스크롤 막대에 작은 빨간색 상자가 표시됩니다. |
| 경고 | `warning` | 위반은 오류 목록 및 명령줄 빌드 출력에 경고로 표시되지만 빌드가 실패하지는 않습니다. | 위반 코드는 녹색 물결선이 밑줄로 표시되고 스크롤 막대에 작은 녹색 상자가 표시됩니다. |
| 정보 | `suggestion` | 위반은 오류 목록에만 메시지로 표시되고 명령줄 빌드 출력에는 표시되지 않습니다. | 위반 코드는 회색 물결선이 밑줄로 표시되고 스크롤 막대에 작은 회색 상자가 표시됩니다. |
| 숨김 | `silent` | 사용자에게 표시되지 않습니다. | 사용자에게 표시되지 않습니다. 그러나 진단은 IDE 진단 엔진에 보고됩니다. |
| None | `none` | 전혀 표시되지 않습니다. | 전혀 표시되지 않습니다. |
| 기본값 | `default` | 규칙의 기본 심각도에 해당합니다. 규칙 기본값을 확인하려면 속성 창을 확인합니다. | 규칙의 기본 심각도에 해당합니다. |

분석기에서 규칙 위반을 발견하면 코드 편집기(위반 코드 아래에 *오류 표시선*이 표시됨) 및 오류 목록 창에 규칙 위반이 보고됩니다.

![오류 목록 창의 분석기 위반](../code-quality/media/code-analysis-error-list.png)

오류 목록에 보고된 분석기 위반은 규칙의 [심각도 수준 설정](../code-quality/use-roslyn-analyzers.md#configure-severity-levels)과 일치합니다. 분석기 위반은 코드 편집기에도 표시되며, 위반 코드 아래에 물결선이 나타납니다. 다음 이미지에는 오류 1개(빨간색 물결선), 경고 1개(녹색 물결선), 제안 1개(회색 점 3개) 등 세 가지 위반이 표시되어 있습니다.

![Visual Studio 코드 편집기의 오류 표시선](media/diagnostics-severity-colors.png)

여러 분석기 규칙 또는 진단에는 규칙 위반을 해결하는 데 적용할 수 있는 하나 이상의 연결된 코드 수정이 있습니다. 코드 수정은 다른 형식의 [빠른 작업](../ide/quick-actions.md)과 함께 전구 아이콘 메뉴에 표시됩니다. 이러한 코드 수정에 대한 정보는 [일반적인 빠른 작업](../ide/quick-actions.md)을 참조하세요.

![분석기 위반 및 빠른 작업 코드 수정](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="configure-analyzer-severity-levels"></a>분석기 심각도 수준 구성

[EditorConfig 파일](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file) 또는 [전구 메뉴](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu)에서 분석기 규칙의 심각도, 즉 진단을 구성할 수 있습니다. 

코드를 빌드 시 검사하고 입력하는 동안 실시간으로 검사하도록 분석기를 구성할 수도 있습니다. 현재 문서에 대해서만 모든 열린 문서 또는 전체 솔루션에 대해 실행되는 라이브 코드 분석의 범위를 구성할 수 있습니다. [방법: 라이브 코드 분석의 범위를 구성합니다](./configure-live-code-analysis-scope-managed-code.md).

> [!TIP]
> 코드 분석기의 빌드 시간 오류 및 경고는 분석기가 NuGet 패키지로 설치된 경우에만 표시됩니다. 기본 제공 분석기(예: IDE0067 및 IDE0068)는 빌드 도중 실행되지 않습니다.

## <a name="nuget-package-versus-vsix-extension"></a>NuGet 패키지와 VSIX 확장 비교

타사 분석기는 NuGet 패키지를 통해 프로젝트별로 설치할 수 있습니다. 일부는 Visual Studio 확장으로도 사용할 수 있으며, 이 경우 Visual Studio에서 여는 모든 솔루션에 적용됩니다. [분석기 설치](../code-quality/install-roslyn-analyzers.md)의 이러한 두 방법 간에 몇 가지 핵심 동작 차이점이 있습니다.

### <a name="scope"></a>Scope

Visual Studio 확장으로 분석기를 설치하는 경우 모든 Visual Studio의 인스턴스에 솔루션 수준에서 적용됩니다. 기본 방법인 NuGet 패키지로 분석기를 설치하는 경우 NuGet 패키지가 설치된 프로젝트에만 적용됩니다. 팀 환경에서 NuGet 패키지로 설치된 분석기는 해당 프로젝트에서 작업하는 *모든 개발자*에 대한 범위에 있습니다.

### <a name="build-errors"></a>빌드 오류

명령줄을 통해 또는 CI(지속적인 통합)의 일부로 빌드 시 규칙을 적용하려면 다음 옵션 중 하나를 선택할 수 있습니다.

- .NET SDK에 기본적으로 분석기를 포함하는 .NET 5.0 프로젝트를 만듭니다. .NET 5.0 이상을 대상으로 하는 프로젝트의 경우 기본적으로 코드 분석을 사용하도록 설정되어 있습니다. [EnableNETAnalyzers](https://docs.microsoft.com/dotnet/core/project-sdk/msbuild-props#enablenetanalyzers) 속성을 true로 설정하여 이전 버전의 .NET을 대상으로 하는 프로젝트에서 코드 분석을 사용하도록 설정할 수 있습니다.

- 분석기를 NuGet 패키지로 설치합니다. 분석기 경고 및 오류는 분석기를 확장으로 설치하는 경우 빌드 보고서에 나타나지 않습니다.

다음 이미지에서는 분석기 규칙 위반을 포함하는 프로젝트 빌드의 명령줄 빌드 출력을 보여줍니다.

![규칙 위반을 사용하여 MSBuild 출력](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>규칙 심각도

Visual Studio 확장으로 설치된 분석기에서 규칙의 심각도를 구성할 수 없습니다. [규칙 심각도](../code-quality/use-roslyn-analyzers.md#configure-severity-levels)를 구성하려면 분석기를 NuGet 패키지로 설치합니다.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [Visual Studio에서 코드 분석기 설치](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Visual Studio에서 코드 분석기 사용](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>추가 정보

- [분석기 FAQ](analyzers-faq.md)
- [사용자 고유의 코드 분석기 작성](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)

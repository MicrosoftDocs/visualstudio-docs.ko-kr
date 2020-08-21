---
title: EditorConfig와 분석기 비교
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b060ae550fd0188728c827cac01c12d51930b57
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88711549"
---
# <a name="code-analysis-faq"></a>코드 분석 FAQ

이 페이지에는 Visual Studio의 .NET Compiler Platform 기반 코드 분석에 대 한 몇 가지 질문과 대답을 포함 합니다.

## <a name="code-analysis-versus-editorconfig"></a>코드 분석 및 EditorConfig

**Q**: 코드 스타일을 확인 하려면 코드 분석 또는 editorconfig를 사용 해야 하나요?

**A**: 코드 분석 및 editorconfig 파일은 직접 작동 합니다. [EditorConfig 파일](../ide/editorconfig-code-style-settings-reference.md) 또는 [텍스트 편집기 옵션](../ide/code-styles-and-code-cleanup.md) 페이지에서 코드 스타일을 정의 하는 경우 실제로는 Visual Studio에 기본 제공 되는 코드 분석기를 구성 하는 것입니다. EditorConfig 파일은 분석기 규칙을 사용 하거나 사용 하지 않도록 설정 하 고 NuGet 분석기 패키지를 구성 하는 데 사용할 수 있습니다.

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig와 규칙 집합 비교

**Q**: 규칙 집합이 나 editorconfig 파일을 사용 하 여 분석기를 구성 해야 하나요?

**A**: 규칙 집합 및 editorconfig 파일은 공존할 수 있으며 분석기를 구성 하는 데 사용할 수 있습니다. EditorConfig 파일 및 규칙 집합을 사용 하 여 규칙을 사용 하거나 사용 하지 않도록 설정 하 고 심각도를 설정할 수 있습니다.

그러나 EditorConfig 파일은 규칙을 구성 하는 또 다른 방법을 제공 합니다.

- .NET 코드 품질 분석기의 경우 EditorConfig 파일을 사용 하 여 [분석할 코드 형식을 정의할](fxcop-analyzer-options.md)수 있습니다.
- Visual Studio에 기본 제공 되는 .NET 코드 스타일 분석기의 경우 EditorConfig 파일을 사용 하 여 코드 베이스에 대해 [기본 설정 된 코드 스타일을 정의할](../ide/editorconfig-code-style-settings-reference.md) 수 있습니다.

규칙 집합 및 EditorConfig 파일 외에도 일부 분석기는 c # 및 VB 컴파일러에 대 한 [추가 파일로](../ide/build-actions.md#build-action-values) 표시 된 텍스트 파일을 사용 하 여 구성 됩니다.

> [!NOTE]
> - EditorConfig 파일은 Visual Studio 2019 버전 16.3 이상에서 규칙을 사용 하도록 설정 하 고 심각도를 설정 하는 데만 사용할 수 있습니다.
> - EditorConfig 파일은 레거시 분석을 구성 하는 데 사용할 수 없지만 규칙 집합은 사용할 수 있습니다.

## <a name="code-analysis-in-ci-builds"></a>CI 빌드에서 코드 분석

**Q**: .NET Compiler Platform 기반 코드 분석은 CI (지속적인 통합) 빌드에서 작동 하나요?

**A**: 예. NuGet 패키지에서 설치 된 분석기의 경우 이러한 규칙은 CI 빌드 중을 포함 하 여 [빌드 시에 적용](roslyn-analyzers-overview.md#build-errors)됩니다. CI 빌드에서 사용 되는 분석기는 규칙 집합과 EditorConfig 파일의 규칙 구성을 모두 고려 합니다. 현재 Visual Studio에 기본 제공 되는 코드 분석기는 NuGet 패키지로 사용할 수 없으므로 이러한 규칙은 CI 빌드에서 시행 되지 않습니다.

## <a name="ide-analyzers-versus-stylecop"></a>IDE 분석기와 StyleCop 비교

**Q**: VISUAL Studio IDE 코드 분석기와 StyleCop 분석기 간의 차이점은 무엇 인가요?

**A**: VISUAL Studio IDE에는 코드 스타일 및 품질 문제를 모두 검색 하는 기본 제공 분석기가 포함 되어 있습니다. 이러한 규칙은 도입 된 새로운 언어 기능을 사용 하 고 코드의 유지 관리 효율성을 향상 시키는 데 도움이 됩니다. IDE 분석기는 Visual Studio 릴리스 마다 지속적으로 업데이트 됩니다.

[StyleCop 분석기](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) 는 코드에서 스타일 일관성을 검사 하는 NuGet 패키지로 설치 된 타사 분석기입니다. 일반적으로 StyleCop 규칙을 사용 하 여 코드 베이스에 대 한 특정 스타일을 권장 하지 않고 개인 기본 설정을 지정할 수 있습니다.

## <a name="code-analyzers-versus-legacy-analysis"></a>코드 분석기와 레거시 분석 비교

**Q**: 레거시 분석과 .NET Compiler Platform 기반 코드 분석의 차이점은 무엇 인가요?

**A**: .NET Compiler Platform 기반 코드 분석은 컴파일 중에 소스 코드를 실시간으로 분석 하는 반면 레거시 분석은 빌드가 완료 된 후 이진 파일을 분석 합니다. 자세한 내용은 [.NET Compiler Platform 기반 분석 및 레거시 분석](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) 및 [FxCop 분석기 FAQ](fxcop-analyzers-faq.md)를 참조 하세요.

## <a name="treat-warnings-as-errors"></a>경고를 오류로 처리

**Q**: 내 프로젝트는 빌드 옵션을 사용 하 여 경고를 오류로 처리 합니다. 레거시 분석에서 원본 코드 분석으로 마이그레이션한 후 모든 코드 분석 경고가 이제 오류로 표시 됩니다. 이를 방지 하려면 어떻게 해야 하나요?

**A**: 코드 분석 경고가 오류로 처리 되지 않도록 하려면 다음 단계를 수행 합니다.

  1. 다음 콘텐츠를 사용 하 여 props 파일을 만듭니다.

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. .Csproj 또는 .vbproj 프로젝트 파일에 줄을 추가 하 여 이전 단계에서 만든 props 파일을 가져옵니다. 이 줄은 FxCop 분석기. props 파일을 가져오는 모든 줄 앞에 배치 해야 합니다. 예를 들어, props 파일 이름이 codeanalysis. props 인 경우:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="code-analysis-solution-property-page"></a>코드 분석 솔루션 속성 페이지

**Q**: 솔루션에 대 한 코드 분석 속성 페이지는 어디에 있나요?

**A**: 보다 안정적인 공유 속성 그룹을 위해 솔루션 수준의 코드 분석 속성 페이지가 제거 되었습니다. 프로젝트 수준에서 코드 분석을 관리 하기 위해 코드 분석 속성 페이지를 계속 사용할 수 있습니다. 관리 되는 프로젝트의 경우 규칙 구성을 위해 규칙 집합에서 EditorConfig로 마이그레이션하는 것이 좋습니다.  솔루션 또는 리포지토리의 여러/모든 프로젝트에서 규칙 집합을 공유 하는 경우 공유 된 props/targets 파일 또는 디렉터리 CodeAnalysisRuleSet 파일에 속성 그룹을 정의 하는 것이 좋습니다. 모든 프로젝트에서 가져오는 이와 같은 일반적인 props 또는 대상이 없는 경우 디렉터리 [또는 하위 디렉터리에 정의 된 모든 프로젝트 파일에서 자동으로 가져오는 최상위 솔루션 디렉터리에 해당 속성 그룹을 추가 하는 것이 좋습니다 .이 디렉터리는 디렉터리 또는 하위 디렉터리에 정의 된 모든 프로젝트 파일에서 자동으로 가져옵니다](https://docs.microsoft.com/visualstudio/msbuild/customize-your-build?directorybuildprops-and-directorybuildtargets).

## <a name="see-also"></a>참고 항목

- [분석기 개요](roslyn-analyzers-overview.md)
- [EditorConfig에 대한 .NET 코딩 규칙 설정](../ide/editorconfig-code-style-settings-reference.md)

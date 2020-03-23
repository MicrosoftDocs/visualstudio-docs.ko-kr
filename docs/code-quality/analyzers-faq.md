---
title: 에디터구성과 분석기
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 680d52ff04553d399b6abeb53919d8aafd4fa792
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79300926"
---
# <a name="code-analysis-faq"></a>코드 분석 자주 묻는 질문

이 페이지에는 Visual Studio의 .NET 컴파일러 플랫폼 기반 코드 분석에 대한 자주 묻는 몇 가지 질문에 대한 답변이 포함되어 있습니다.

## <a name="code-analysis-versus-editorconfig"></a>코드 분석 대 편집기 구성

**Q**: 코드 스타일을 확인하기 위해 코드 분석 또는 EditorConfig를 사용해야합니까?

**A**: 코드 분석 및 편집기구성 파일은 함께 작동합니다. [EditorConfig 파일](../ide/editorconfig-code-style-settings-reference.md) 또는 [텍스트 편집기 옵션](../ide/code-styles-and-code-cleanup.md) 페이지에서 코드 스타일을 정의할 때 Visual Studio에 내장된 코드 분석기를 실제로 구성합니다. EditorConfig 파일을 사용하여 분석기 규칙을 활성화 또는 비활성화하고 [FxCop 분석기와](configure-fxcop-analyzers.md)같은 일부 NuGet 분석기 패키지를 구성할 수도 있습니다.

## <a name="editorconfig-versus-rule-sets"></a>편집기 구성 및 규칙 집합 비교

**Q**: 규칙 집합 또는 EditorConfig 파일을 사용하여 분석기를 구성해야 합니까?

**A**: 규칙 집합과 EditorConfig 파일이 공존할 수 있으며 분석기를 구성하는 데 사용할 수 있습니다. EditorConfig 파일과 규칙 집합을 모두 사용하면 규칙을 활성화 및 비활성화하고 심각도를 설정할 수 있습니다.

그러나 EditorConfig 파일은 규칙을 구성하는 추가 방법도 제공합니다.

- FxCop 분석기의 경우 EditorConfig 파일을 사용하면 [분석할 코드 유형을 정의할 수](fxcop-analyzer-options.md)있습니다.
- Visual Studio에 내장된 코드 스타일 분석기의 경우 EditorConfig 파일을 사용하면 코드베이스에 대해 [선호하는 코드 스타일을 정의할](../ide/editorconfig-code-style-settings-reference.md) 수 있습니다.

규칙 집합 및 EditorConfig 파일 외에도 일부 분석기는 C# 및 VB 컴파일러의 [추가 파일로](../ide/build-actions.md#build-action-values) 표시된 텍스트 파일을 사용하여 구성됩니다.

> [!NOTE]
> - EditorConfig 파일은 Visual Studio 2019 버전 16.3 이상에서 규칙을 활성화하고 심각도를 설정하는 데만 사용할 수 있습니다.
> - EditorConfig 파일은 레거시 분석을 구성하는 데 사용할 수 없지만 규칙 집합은 구성할 수 있습니다.

## <a name="code-analysis-in-ci-builds"></a>CI 빌드의 코드 분석

**Q**: .NET 컴파일러 플랫폼 기반 코드 분석이 CI(연속 통합) 빌드에서 작동합니까?

**A**: 예. NuGet 패키지에서 설치된 분석기의 경우 이러한 규칙은 CI 빌드 중을 포함하여 [빌드 시 적용됩니다.](roslyn-analyzers-overview.md#build-errors) CI에 사용되는 분석기는 규칙 집합과 EditorConfig 파일 모두에서 규칙 구성을 존중합니다. 현재 Visual Studio에 내장된 코드 분석기는 NuGet 패키지로 사용할 수 없으므로 CI 빌드에서 이러한 규칙을 적용할 수 없습니다.

## <a name="ide-analyzers-versus-stylecop"></a>IDE 분석기 대 스타일콥

**Q**: 비주얼 스튜디오 IDE 코드 분석기와 StyleCop 분석기의 차이점은 무엇입니까?

**A**: Visual Studio IDE에는 코드 스타일과 품질 문제를 모두 찾는 기본 제공 분석기가 포함되어 있습니다. 이러한 규칙은 새로운 언어 기능을 도입할 때 사용하고 코드의 유지 관리 가능성을 개선하는 데 도움이 됩니다. IDE 분석기는 각 Visual Studio 릴리스마다 지속적으로 업데이트됩니다.

[StyleCop 분석기는](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) 코드의 스타일 일관성을 확인하는 NuGet 패키지로 설치된 타사 분석기입니다. 일반적으로 StyleCop 규칙을 사용하면 한 스타일을 다른 스타일보다 권장하지 않고 코드 베이스에 대한 개인 기본 설정을 설정할 수 있습니다.

## <a name="code-analyzers-versus-legacy-analysis"></a>코드 분석기 와 레거시 분석

**Q**: 레거시 분석과 .NET 컴파일러 플랫폼 기반 코드 분석의 차이점은 무엇입니까?

**A**: .NET 컴파일러 플랫폼 기반 코드 분석은 실시간으로 컴파일하는 동안 소스 코드를 분석하지만 레거시 분석은 빌드가 완료된 후 이진 파일을 분석합니다. 자세한 내용은 [.NET 컴파일러 플랫폼 기반 분석과 레거시 분석 및](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) [FxCop 분석기 FAQ를](fxcop-analyzers-faq.md)참조하십시오.

## <a name="treat-warnings-as-errors"></a>경고를 오류로 처리

**Q**: 내 프로젝트는 빌드 옵션을 사용하여 경고를 오류로 처리합니다. 레거시 분석에서 소스 코드 분석으로 마이그레이션한 후 모든 코드 분석 경고가 오류로 나타납니다. 어떻게 예방할 수 있습니까?

**A**: 코드 분석 경고가 오류로 처리되지 않도록 하려면 다음 단계를 따르십시오.

  1. 다음 내용이 있는 .props 파일을 만듭니다.

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. .csproj 또는 .vbproj 프로젝트 파일에 줄을 추가하여 이전 단계에서 만든 .props 파일을 가져옵니다. 이 줄은 FxCop 분석기 .props 파일을 가져오는 모든 줄 앞에 배치되어야 합니다. 예를 들어 .props 파일이름이 codeanalysis.props인 경우:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="see-also"></a>참고 항목

- [분석기 개요](roslyn-analyzers-overview.md)
- [편집기구성에 대한 .NET 코딩 규칙 설정](../ide/editorconfig-code-style-settings-reference.md)

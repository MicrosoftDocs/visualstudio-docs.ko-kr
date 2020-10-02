---
title: 코드 분석 규칙 집합
ms.date: 04/02/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47019ecd01a4ad432a853a7f1a4f7d7112be163c
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659207"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>규칙 집합을 사용 하 여 코드 분석 규칙 그룹화

Visual Studio에서 코드 분석을 구성 하는 경우 기본 제공 *규칙 집합*목록에서 선택할 수 있습니다. 규칙 집합은 대상 문제 및 해당 프로젝트에 대 한 특정 조건을 식별 하는 코드 분석 규칙의 그룹입니다. 예를 들어 공개적으로 사용 가능한 Api에 대 한 코드를 검사 하도록 디자인 된 규칙 집합을 적용할 수 있습니다. 사용 가능한 모든 규칙을 포함 하는 규칙 집합을 적용할 수도 있습니다.

규칙을 추가 또는 삭제 하거나 규칙 심각도를 변경 하 여 **오류 목록**에서 경고나 오류로 표시 되도록 규칙 집합을 사용자 지정할 수 있습니다. 사용자 지정 된 규칙 집합은 특정 개발 환경에 대 한 요구 사항을 충족할 수 있습니다. 규칙 집합을 사용자 지정할 때 규칙 집합 편집기는 프로세스에 도움이 되는 검색 및 필터링 도구를 제공 합니다.

규칙 집합은 [관리 코드 분석](/dotnet/fundamentals/code-analysis/code-quality-rule-options), [관리 코드의 레거시 분석](how-to-configure-code-analysis-for-a-managed-code-project.md)및 [c + + 코드 분석](/cpp/code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run)에 사용할 수 있습니다.

## <a name="rule-set-format"></a>규칙 집합 형식

규칙 집합은 *.* 규칙 집합 파일의 XML 형식으로 지정 됩니다. ID 및 *작업*으로 구성 되는 규칙은 파일의 분석기 ID 및 네임 스페이스로 그룹화 됩니다.

*. 규칙 집합* 파일의 내용은 다음 XML과 유사 합니다.

```xml
<RuleSet Name="Rules for Hello World project" Description="These rules focus on critical issues for the Hello World app." ToolsVersion="10.0">
  <Localization ResourceAssembly="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.dll" ResourceBaseName="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.Localized">
    <Name Resource="HelloWorldRules_Name" />
    <Description Resource="HelloWorldRules_Description" />
  </Localization>
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1009" Action="Warning" />
    <Rule Id="CA1016" Action="Warning" />
    <Rule Id="CA1033" Action="Warning" />
  </Rules>
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1802" Action="Error" />
    <Rule Id="CA1814" Action="Info" />
    <Rule Id="CA1823" Action="None" />
    <Rule Id="CA2217" Action="Warning" />
  </Rules>
</RuleSet>
```

> [!TIP]
> 그래픽 **규칙 집합 편집기** 의 [규칙 집합을 직접 편집](../code-quality/working-in-the-code-analysis-rule-set-editor.md) 하는 것이 더 쉽습니다.

## <a name="specify-a-rule-set-for-a-project"></a>프로젝트에 대 한 규칙 집합 지정

프로젝트에 대 한 규칙 집합은 Visual Studio 프로젝트 파일의 **CodeAnalysisRuleSet** 속성으로 지정 됩니다. 예를 들면 다음과 같습니다.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>참조

- [코드 분석 규칙 집합 참조](../code-quality/rule-set-reference.md)

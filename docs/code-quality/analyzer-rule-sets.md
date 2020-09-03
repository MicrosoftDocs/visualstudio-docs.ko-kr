---
title: FxCop 분석기 규칙 집합 및 editorconfig 파일
ms.date: 10/08/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11b99bb08c82725f19f7985a97656edf65f112d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88800218"
---
# <a name="enable-a-category-of-rules"></a>규칙 범주 사용

분석기 패키지는 보안 또는 설계 규칙과 같은 규칙 범주를 빠르고 쉽게 사용할 수 있도록 미리 정의 된 [Editorconfig](use-roslyn-analyzers.md#rule-severity) 및 [규칙 집합](using-rule-sets-to-group-code-analysis-rules.md) 파일을 포함할 수 있습니다. [FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) NuGet analyzer 패키지에는 규칙 집합 (버전 2.6.2 critical부터 시작) 및 editorconfig 파일 (버전 2.9.5부터 시작)이 모두 포함 되어 있습니다. 규칙의 특정 범주를 사용 하도록 설정 하면 대상 문제 및 특정 조건을 식별할 수 있습니다.

> [!NOTE]
> Visual Studio 2019 버전 16.3부터 분석기 규칙을 사용 하도록 설정 하 고 EditorConfig 파일을 사용 하 여 심각도를 설정 하는 것이 지원 됩니다.

FxCop analyzer NuGet 패키지에는 다음 규칙 범주에 대 한 미리 정의 된 규칙 집합 및 EditorConfig 파일이 포함 되어 있습니다.

- 모든 규칙
- 데이터 흐름
- 디자인
- 설명서
- 전역화
- 상호 운용성
- 유지 관리
- 이름 지정
- 성능
- FxCop에서 이식
- 안정성
- 보안
- 사용량

이러한 각 규칙 범주에는 다음에 대 한 EditorConfig 또는 rule set 파일이 있습니다.

- 범주에 있는 모든 규칙을 사용 하도록 설정 하 고 다른 모든 규칙을 사용 하지 않도록 설정 합니다.
- 각 규칙의 기본 심각도 및 사용 설정 사용 (및 기타 모든 규칙 사용 안 함)

> [!TIP]
> "모든 규칙" 범주에는 모든 규칙을 사용 하지 않도록 설정 하는 추가 EditorConfig 또는 규칙 집합 파일이 있습니다. 이 파일을 사용 하 여 프로젝트에서 분석기 경고 또는 오류를 신속 하 게 제거할 수 있습니다.

> [!TIP]
> 레거시 "FxCop" 분석에서 .NET Compiler Platform 기반 코드 분석으로 마이그레이션하는 경우 EditorConfig 및 규칙 집합 파일을 사용 하 여 [이전에 사용한](rule-set-reference.md)것과 비슷한 규칙 구성을 계속 해 서 사용할 수 있습니다.

## <a name="predefined-editorconfig-files"></a>미리 정의 된 EditorConfig 파일

FxCopAnalyzers analyzer 패키지에 대해 미리 정의 된 EditorConfig 파일은 *% USERPROFILE% \\ . nuget\packages\microsoft.codeanalysis.fxcopanalyzers \\ \<version\> \editorconfig* 디렉터리에 있습니다. 예를 들어 모든 보안 규칙을 사용 하도록 설정 하는 EditorConfig 파일은 *% USERPROFILE% \\ . Nuget\packages\microsoft.codeanalysis.fxcopanalyzers \\ \<version\> \\ Orom\omom\securityststststststst\securitystc\securityst\*

선택한 editorconfig 파일을 프로젝트의 루트 디렉터리에 복사 합니다.

## <a name="predefined-rule-sets"></a>미리 정의된 규칙 집합

FxCopAnalyzers analyzer 패키지에 대 한 미리 정의 된 규칙 집합 파일은 *% USERPROFILE% \\ . nuget\packages\microsoft.codeanalysis.fxcopanalyzers \\ \<version\> \\ststl* 디렉터리에 있습니다. 예를 들어 모든 보안 규칙을 사용 하도록 설정 하는 규칙 집합 파일은 *% USERPROFILE% \\ . nuget\packages\microsoft.codeanalysis.fxcopanalyzers \\ \<version\> \rulesets\SecurityRulesEnabled.ruleset*에 있습니다.

하나 이상의 규칙 집합을 복사 하 고 Visual Studio 프로젝트를 포함 하는 디렉터리 또는 **솔루션 탐색기**에 직접 붙여 넣습니다.

[미리 정의 된 규칙 집합](how-to-create-a-custom-rule-set.md) 을 기본 설정으로 사용자 지정할 수도 있습니다. 예를 들어 위반이 **오류 목록**에 오류 또는 경고로 표시 되도록 하나 이상의 규칙의 심각도를 변경할 수 있습니다.

### <a name="set-the-active-rule-set"></a>활성 규칙 집합 설정

활성 규칙 집합을 설정 하는 프로세스는 .NET Core/.NET Standard 프로젝트 또는 .NET Framework 프로젝트가 있는지 여부에 따라 약간 다릅니다.

#### <a name="net-core"></a>.NET Core

규칙을 .NET Core 또는 .NET Standard 프로젝트의 분석에 대해 활성 규칙 집합으로 설정 하려면 **CodeAnalysisRuleSet** 속성을 프로젝트 파일에 수동으로 추가 합니다. 예를 들어 다음 코드 조각은 `HelloWorld.ruleset` 활성 규칙 집합으로 설정 됩니다.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

#### <a name="net-framework"></a>.NET Framework

규칙을 .NET Framework 프로젝트의 분석을 위한 활성 규칙 집합으로 설정 하려면 다음을 수행 합니다.

- **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.

- 프로젝트 속성 페이지에서 **코드 분석** 탭을 선택 합니다.

::: moniker range="vs-2017"

- **이 규칙 집합 실행**에서 **찾아보기**를 선택한 다음 프로젝트 디렉터리에 복사한 원하는 규칙 집합을 선택 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

- **활성 규칙**에서 **찾아보기**를 선택한 다음 프로젝트 디렉터리에 복사한 원하는 규칙 집합을 선택 합니다.

::: moniker-end

   이제 선택한 규칙 집합에서 사용 하도록 설정 된 규칙에 대 한 규칙 위반만 표시 됩니다.

## <a name="see-also"></a>참고 항목

- [분석기 FAQ](analyzers-faq.md)
- [.NET Compiler Platform 분석기 개요](roslyn-analyzers-overview.md)
- [분석기 설치](install-roslyn-analyzers.md)
- [분석기 구성](use-roslyn-analyzers.md)
- [규칙 집합을 사용 하 여 코드 분석 규칙 그룹화](using-rule-sets-to-group-code-analysis-rules.md)

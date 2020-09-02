---
title: 사용자 지정 코드 분석 규칙 집합 만들기
ms.date: 11/02/2018
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a4659efef9b233284a593fecd5c8404cb2650b0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88893270"
---
# <a name="customize-a-rule-set"></a>규칙 집합 사용자 지정

코드 분석에 대 한 특정 프로젝트 요구 사항을 충족 하도록 사용자 지정 규칙 집합을 만들 수 있습니다.

## <a name="create-a-custom-rule-set-from-an-existing-rule-set"></a>기존 규칙 집합에서 사용자 지정 규칙 집합 만들기

사용자 지정 규칙 집합을 만들려면 **규칙 집합 편집기**에서 기본 제공 규칙 집합을 열 수 있습니다. 여기에서 특정 규칙을 추가 또는 제거 하 고, 규칙을 위반할 때 발생 하는 동작을 변경할 수 있습니다 &mdash; . 예를 들어 경고 또는 오류를 표시할 수 있습니다.

1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 선택 합니다.

2. **속성** 페이지에서 **코드 분석** 탭을 선택 합니다.

::: moniker range="vs-2017"

3. **이 규칙 집합 실행** 드롭다운 목록에서 다음 중 하나를 수행 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

3. **활성 규칙** 드롭다운 목록에서 다음 중 하나를 수행 합니다.

::: moniker-end

   - 사용자 지정하려는 규칙 집합을 선택합니다.

     \- 또는 -

   - **\<Browse>** 목록에 없는 기존 규칙 집합을 지정 하려면 선택 합니다.

4. **열기** 를 선택 하 여 규칙 집합 편집기에서 규칙을 표시 합니다.

> [!NOTE]
> .NET Core 또는 .NET Standard 프로젝트인 경우 **코드 분석** 속성 탭이 없기 때문에 프로세스는 약간 다릅니다. 단계에 따라 [미리 정의 된 규칙 집합을 프로젝트에 복사 하 고 활성 규칙 집합으로 설정](analyzer-rule-sets.md)합니다. 규칙 집합을 복사한 후에는 **솔루션 탐색기**에서 열어 [Visual Studio 규칙 집합 편집기에서 편집할](working-in-the-code-analysis-rule-set-editor.md) 수 있습니다.

## <a name="create-a-new-rule-set"></a>새 규칙 집합 만들기

**새 파일** 대화 상자에서 새 규칙 집합 파일을 만들 수 있습니다.

1. **파일**  >  **새로 만들기**  >  **파일**을 선택 하거나 **ctrl** + **N**을 누릅니다.

2. **새 파일** 대화 상자에서 왼쪽의 **일반** 범주를 선택한 다음 **코드 분석 규칙 집합**을 선택 합니다.

3. **열기**를 선택합니다.

   새 규칙 집합 파일이 규칙 집합 편집기에서 *열립니다.*

## <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>여러 규칙 집합에서 사용자 지정 규칙 집합 만들기

> [!NOTE]
> 다음 절차는 **코드 분석** 속성 탭이 없는 .net Core 프로젝트에는 적용 되지 않습니다.

1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 선택 합니다.

2. **속성** 페이지에서 **코드 분석** 탭을 선택 합니다.

::: moniker range="vs-2017"

3. **\<Choose multiple rule sets>** **이 규칙 집합 실행**에서 선택 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

3. **\<Choose multiple rule sets>** **활성 규칙**에서 선택 합니다.

::: moniker-end

4. **규칙 집합 추가 또는 제거** 대화 상자에서 새 규칙 집합에 포함할 규칙 집합을 선택 합니다.

   ![규칙 집합 추가 또는 제거 대화 상자](media/add-remove-rule-sets.png)

5. 다른 이름 **으로 저장**을 선택 하 고, *. 규칙 집합* 파일의 이름을 입력 한 다음, **저장**을 선택 합니다.

   **이 규칙 집합 실행** 목록에서 새 규칙 집합이 선택 됩니다.

6. **열기** 를 선택 하 여 규칙 집합 편집기에서 새 규칙 집합을 엽니다.

## <a name="rule-precedence"></a>규칙 우선 순위

- 심각도가 다른 규칙 집합에서 같은 규칙이 두 번 이상 나열 되는 경우 컴파일러에서 오류를 생성 합니다. 예를 들면 다음과 같습니다.

   ```xml
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" />
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

- 동일한 규칙이 심각도가 *같은* 규칙 집합에서 두 번 이상 나열 되는 경우 **오류 목록**에 다음 경고가 표시 될 수 있습니다.

   **CA0063: 규칙 집합 파일 ' your \[ ]. 규칙 집합 또는 종속 규칙 집합 파일 중 하나를 로드 하지 못했습니다. 파일이 규칙 집합 스키마를 따르지 않습니다.**

- 규칙 집합에 **include** 태그를 사용 하 여 자식 규칙 집합이 포함 되어 있고 자식 및 부모 규칙에서 둘 다 동일한 규칙을 나열 하지만 심각도가 다른 경우 부모 규칙 집합의 심각도가 우선적으로 적용 됩니다. 예를 들면 다음과 같습니다.

   ```xml
   <!-- Parent rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Include Path="classlibrary_child.ruleset" Action="Default" />
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" /> <!-- Overrides CA1021 severity from child rule set -->
     </Rules>
   </RuleSet>

   <!-- Child rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules from child" Description="Code analysis rules from child." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

## <a name="name-and-description"></a>이름 및 설명

편집기에 열려 있는 규칙 집합의 표시 이름을 변경 하려면 **Properties** 메뉴 **View**  >  모음에서**속성 창** 보기를 선택 하 여 속성 창을 엽니다. **이름** 상자에 표시 이름을 입력 합니다. 규칙 집합에 대 한 설명을 입력할 수도 있습니다.

## <a name="next-steps"></a>다음 단계

규칙 집합을 만들었으므로 다음 단계는 규칙을 추가 또는 제거 하거나 규칙 위반의 심각도를 수정 하 여 규칙을 사용자 지정 하는 것입니다.

> [!div class="nextstepaction"]
> [규칙 집합 편집기에서 규칙 수정](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>추가 정보

- [방법: 관리 코드 프로젝트에 대한 코드 분석 구성](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [코드 분석 규칙 집합 참조](../code-quality/rule-set-reference.md)

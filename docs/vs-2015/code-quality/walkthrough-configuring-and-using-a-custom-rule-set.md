---
title: '연습: 사용자 지정 규칙 집합 구성 및 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8239afd1cf4e8c0a5e702f2b0e4ed64408cada09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645746"
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>연습: 사용자 지정 규칙 집합 구성 및 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 클래스 라이브러리에 대해 사용자 지정 된 *규칙 집합* 을 사용 하도록 구성 된 코드 분석 도구를 사용 하는 방법을 보여 줍니다. 솔루션에 대해 지정한 프로젝트 형식과 관련 된 규칙 집합을 선택 하거나, 다른 규칙 집합을 선택 하 여 다른 방법으로 수정할 수 있는 문제에 대 한 레거시 코드 검색과 같은 특정 요구 사항을 충족 시킬 수 있습니다. 두 경우 모두, 규칙 집합을 사용자 지정 하 여 프로젝트 요구 사항에 맞게 조정할 수도 있습니다.

 이 연습에서는 다음 프로세스를 단계별로 수행 합니다.

- 클래스 라이브러리를 만듭니다.

- **Microsoft 기본 디자인 지침 규칙** 코드 분석 규칙 집합을 선택 합니다.

- 클래스에 사용자 고유의 코드를 추가 합니다.

- 코드 분석을 실행 합니다.

- 규칙 집합을 사용자 지정 합니다.

- 코드 분석을 실행 하 고 규칙 집합 사용자 지정 동작의 작동 방식을 확인 합니다.

## <a name="prerequisites"></a>필수 구성 요소

- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]또는 [!INCLUDE[vsPro](../includes/vspro-md.md)]

## <a name="using-rule-sets-with-code-analysis"></a>코드 분석에 규칙 집합 사용
 먼저 간단한 클래스 라이브러리를 만듭니다.

#### <a name="create-a-class-library"></a>클래스 라이브러리 만들기

1. **파일** 메뉴에서 **새로 만들기**를 클릭하고 **프로젝트**를 클릭합니다.

2. **새 프로젝트** 대화 상자의 **프로젝트 형식**에서 **Visual c #** 을 클릭 합니다.

3. **Visual c #** 에서 **클래스 라이브러리**를 선택 합니다.

4. **이름** 텍스트 상자에 **rulesetsample** 을 입력 한 다음 **확인**을 클릭 합니다.

   다음으로 **Microsoft 기본 디자인 지침 규칙** 규칙 집합을 선택 하 고 프로젝트와 함께 저장 합니다.

#### <a name="select-a-code-analysis-rule-set"></a>코드 분석 규칙 집합 선택

1. **분석** 메뉴에서 **rulesetsample에 대 한 코드 분석 구성**을 클릭 합니다.

    코드 분석에 대 한 구성 설정이 표시 됩니다.

2. **이 규칙 집합 실행** 드롭다운 목록에서 **Microsoft 모든 규칙**을 선택 합니다.

    사용 가능한 규칙 집합에 대 한 자세한 내용은 [코드 분석 규칙 집합 참조](../code-quality/code-analysis-rule-set-reference.md)를 참조 하세요.

    파일 메뉴에서 선택한 **항목 저장** 을 클릭 하 여 선택한 규칙 집합 및 해당 설정에 대 한 정보를 사용 하 여 프로젝트 파일을 업데이트 합니다.

   > [!TIP]
   > 실제 상황에서 코드 분석을 사용 하 여 대상으로 지정할 문제를 우선 순위를 정하는 데 사용 하는 것이 좋은 방법입니다. **권장 되는 최소 규칙** 규칙 집합으로 시작 하 여 원하는 문제를 해결 한 다음, 더 많은 규칙 또는 규칙 집합을 추가 하 여 추가 문제를 찾아 수정 하는 것입니다.

   다음으로, "식별자의 철자가 정확 해야 합니다." 코드 분석 규칙의 위반을 설명 하는 데 사용 되는 일부 코드를 클래스 라이브러리에 추가 합니다. 자세한 내용은 [CA1704: identifier의 철자가](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)정확한 지 확인 하세요.

#### <a name="add-your-own-code"></a>사용자 고유의 코드 추가

- 솔루션 탐색기에서 Class1.cs 파일을 열고 기존 코드를 다음으로 바꿉니다.

  ```
  using System;
  using System.Collections.Generic;
  using System.Text;

  namespace RuleSetSample
  {
      public class Class1
      {
          //The variable parameter names "a" and "b" will cause
          //the warning CA 1704 Microsoft.Naming "Consider
          //providing a more meaningful name" to fire
          public int AddIntegers(int a, int b)
          {

              int sum = a + b;

              return (sum);
          }
      }
  }

  ```

  이제 RuleSetSample 프로젝트에 대해 코드 분석을 실행 하 고 오류 목록 창에서 생성 된 오류 및 경고를 찾을 수 있습니다.

#### <a name="run-code-analysis-on-the-rulesetsample-project"></a>RuleSetSample 프로젝트에서 코드 분석 실행

1. **분석** 메뉴에서 **rulesetsample에 대 한 코드 분석 실행**을 클릭 합니다.

2. 오류 목록 창에서 **경고** 를 클릭 한 다음 **설명** 열 머리글을 클릭 하 여 사전순으로 경고를 정렬 합니다.

    실제 응용 프로그램에서는이 시점에서 수정할 수 있는 모든 규칙 위반을 수정 하거나, 필요에 따라 수정 하는 것이 충분 하지 않다고 판단 되는 경우 규칙을 해제 하거나 표시 하지 않을 수 있습니다. 자세한 내용은 [SuppressMessage 특성을 사용하여 경고 표시 안 함](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)을 참조하세요.

3. CA1704 경고를 확인 합니다. 이 규칙에 대 한 이러한 위반은 "매개 변수에 대 한 보다 의미 있는 이름을 제공 해야 합니다." 라는 것을 의미 합니다. 다음 절차에 설명 된 대로 코드에서 문제를 수정 하거나 규칙을 사용 하지 않도록 설정할 수 있습니다.

   다음으로, 규칙 집합을 사용자 지정 하 여 CA1704 경고를 제외 하 고 "식별자의 철자가 정확 해야 합니다." 라는 메시지가 표시 됩니다.

#### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>프로젝트에 대 한 규칙 집합을 사용자 지정 하 여 특정 규칙을 사용 하지 않도록 설정

1. **분석** 메뉴에서 **rulesetsample에 대 한 코드 분석 구성**을 클릭 합니다.

2. **이 규칙 집합 실행** 드롭다운 목록에서 **Microsoft 모든 규칙** 규칙 집합이 강조 표시 되어 있는지 확인 한 다음 **열기**를 클릭 합니다. 규칙 집합 페이지가 표시 됩니다.

3. Microsoft. 명명 범주 노드를 확장 한 다음 CA1704 경고를 선택 합니다.

4. **작업** 열에서 없음을 선택 **합니다.** 이렇게 하면 CA1704가 오류 목록 창에서 경고나 오류로 표시 되지 않습니다.

    이제 다양 한 도구 모음 단추 및 필터링 옵션을 시험해 보고이에 익숙해질 수 있습니다. 예를 들어 **묶는 방법** 드롭다운 목록을 사용 하 여 특정 규칙 또는 규칙 범주를 쉽게 찾을 수 있습니다. 또 다른 예는 규칙 집합 페이지 도구 모음에서 **사용할 수 없는 규칙 숨기기** 단추를 사용 하 여 **작업** 열이 **없음**으로 설정 된 모든 규칙을 숨기 거 나 표시할 수 있다는 것입니다. 이는 사용 하지 않도록 설정 된 규칙을 검색 하 여 사용 하지 않도록 설정 하려는 경우에 유용할 수 있습니다.

5. 보기 메뉴에서 속성 창을 클릭합니다. 속성 도구 창의 이름 상자에 **내 사용자 지정 규칙 집합** 을 입력 합니다. 이렇게 하면 IDE에서 새 규칙 집합의 표시 이름이 변경 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 됩니다.

6. **파일** 메뉴에서 **Microsoft 모든 규칙을 저장 합니다.** 규칙 집합을 클릭 하 여 사용자 지정 규칙 집합을 저장 합니다. 프로젝트의 루트 폴더로 이동 합니다. **파일 이름** 텍스트 상자에 **mycustomruleset 집합**을 입력 합니다. 이제 사용자 지정 규칙 집합을 프로젝트에 사용할 수 있도록 선택할 수 있습니다.

   새 규칙 집합을 만든 후 이제 새 규칙 집합을 사용할 수 있도록 프로젝트 설정을 구성 해야 합니다.

#### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>프로젝트에 사용할 새 규칙 집합 지정

1. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 선택 합니다.

2. **속성** 탭에서 **코드 분석**을 클릭 합니다.

    **이 규칙 집합 실행** 드롭다운 목록에서을 클릭 **\<Browse..>** 합니다. 코드 프로젝트의 루트 폴더로 이동한 다음 **Mycustomruleset**집합을 선택 합니다. 이전 절차에서 만든 새 규칙 집합입니다.

3. **파일** 메뉴에서 **저장** 을 클릭 하 여 프로젝트 구성을 저장 합니다. 이제 사용자 지정 규칙 집합을 프로젝트와 함께 사용할 수 있습니다.

   마지막으로 MyCustomRuleSet 규칙 집합을 사용 하 여 코드 분석을 다시 실행 합니다. 오류 목록 창에는 CA1704 성능 규칙 위반이 표시 되지 않습니다.

#### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>RuleSetSample 프로젝트에 대 한 코드 분석을 두 번 실행 합니다.

1. **분석** 메뉴에서 **rulesetsample에 대 한 코드 분석 실행**을 클릭 합니다.

2. 오류 목록 창에서 **경고**를 클릭 하면 "식별자에 올바른 철자를 입력 해야 합니다." 규칙에 대 한 CA1704 warning 위반이 더 이상 표시 되지 않습니다.

## <a name="see-also"></a>관련 항목
 [방법: 관리 코드에 대 한 코드 분석 구성 프로젝트](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md) [코드 분석 규칙 집합 참조](../code-quality/code-analysis-rule-set-reference.md)

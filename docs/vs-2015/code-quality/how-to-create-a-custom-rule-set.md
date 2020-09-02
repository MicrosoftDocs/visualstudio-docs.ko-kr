---
title: '방법: 사용자 지정 규칙 집합 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6e4aef02a2bb320112d7d268da28cf66b1ec6751
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657443"
---
# <a name="how-to-create-a-custom-rule-set"></a>방법: 사용자 지정 규칙 집합 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsUltShort](../includes/vsultshort-md.md)], [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] 및에서는 [!INCLUDE[vsPro](../includes/vspro-md.md)] 코드 분석과 관련 된 특정 프로젝트 요구 사항에 맞게 사용자 지정 *규칙 집합* 을 만들고 수정할 수 있습니다. 사용자 지정 규칙 집합을 만들려면 규칙 집합 편집기에서 하나 이상의 표준 규칙 집합을 엽니다. 그런 다음 특정 규칙을 추가 하거나 제거 하 고, 코드 분석에서 규칙이 위반 된 것으로 확인 될 때 발생 하는 작업을 변경할 수 있습니다.

 새 사용자 지정 규칙 집합을 만들려면 새 파일 이름을 사용 하 여 저장 합니다. 사용자 지정 규칙 집합이 프로젝트에 자동으로 할당 됩니다.

## <a name="opening-the-rule-set-editor"></a>규칙 집합 편집기 열기

#### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>규칙 집합 편집기에서 빈 규칙 집합 파일을 열려면

1. 의 **파일** 메뉴에서 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **새로 만들기** 를 가리킨 다음 **파일**을 클릭 합니다.

2. **새 파일** 대화 상자의 **설치 된 템플릿** 목록에서 **일반** 을 클릭 한 다음 **코드 분석 규칙 집합**을 선택 합니다.

3. 규칙 집합 편집기가 나타납니다. 편집기 목록에서 규칙이 선택 되지 않습니다.

#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>기존 규칙 집합 하나에서 사용자 지정 규칙을 만들려면

1. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 선택 합니다.

2. **속성** 탭에서 **코드 분석**을 클릭 합니다.

3. **규칙 집합** 드롭다운 목록에서 다음 중 하나를 수행 합니다.

   - 사용자 지정 하려는 규칙 집합을 선택 합니다.

     \- 또는 -

   - **\<Browse...>** 목록에 없는 기존 규칙 집합을 지정 하려면 선택 합니다.

4. **열기** 를 클릭 하 여 규칙 집합 편집기에서 규칙을 표시 합니다.

#### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>여러 기존 규칙 집합에서 사용자 지정 규칙 집합을 만들려면

1. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 선택 합니다.

2. **속성** 탭에서 **코드 분석**을 클릭 합니다.

3. **\<Choose multiple rule sets...>** **이 규칙 집합 실행**에서 선택 합니다.

4. **규칙 집합 추가 또는 제거** 대화 상자에서 새 규칙 집합의 기반으로 사용할 규칙 집합을 선택 하 고 **확인**을 클릭 합니다.

5. 새 규칙 집합을 저장 합니다.

     새 규칙 집합의 이름은 **이 규칙 집합 실행** 목록에서 선택 됩니다. 다음 단계에서 규칙 집합의 표시 이름을 변경할 수 있습니다.

6. 필드 규칙 집합의 표시 이름을 변경 하려면 **보기** 메뉴에서 **속성 창**을 클릭 합니다. **이름** 상자에 표시 이름을 입력 합니다.

7. 새 규칙 집합에서 특정 코드 분석 규칙을 추가, 제거 또는 수정 하려면 **열기**를 클릭 합니다.

## <a name="modifying-a-rule-set"></a>규칙 집합 수정

#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>규칙 집합 편집기에서 규칙 집합을 수정 하려면

- 규칙 집합의 표시 이름을 변경 하려면 **보기** 메뉴에서 **속성 창**을 클릭 합니다. **이름** 상자에 표시 이름을 입력 합니다. 표시 이름은 파일 이름과 다를 수 있습니다.

- 그룹의 모든 규칙을 사용자 지정 규칙 집합에 추가 하려면 그룹의 확인란을 선택 합니다. 그룹의 모든 규칙을 제거 하려면 확인란의 선택을 취소 합니다.

- 사용자 지정 규칙 집합에 특정 규칙을 추가 하려면 규칙의 확인란을 선택 합니다. 규칙 집합에서 규칙을 제거 하려면 확인란의 선택을 취소 합니다.

- 코드 분석에서 규칙을 위반할 때 수행 되는 동작을 변경 하려면 규칙에 대 한 **작업** 필드를 클릭 하 고 다음 값 중 하나를 선택 합니다.

     **Warn** -경고를 생성 합니다.

     **오류** -오류를 생성 합니다.

     **없음** -규칙을 사용 하지 않도록 설정 합니다. 이 동작은 규칙 집합에서 규칙을 제거 하는 것과 같습니다.

## <a name="changing-the-rule-set-editor-display"></a>규칙 집합 편집기 표시 변경

#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>규칙 집합 편집기 도구 모음을 사용 하 여 규칙 집합 편집기에서 필드를 그룹화, 필터링 또는 변경 하려면

- 모든 그룹의 규칙을 확장 하려면 **모두 확장**을 클릭 합니다.

- 모든 그룹의 규칙을 축소 하려면 **모두 축소**를 클릭 합니다.

- 규칙을 그룹화 하는 필드를 변경 하려면 **그룹화** 방법 목록에서 필드를 선택 합니다. 규칙을 그룹화 하지 않고 표시 하려면를 선택 **\<None>** 합니다.

- 규칙 열에서 필드를 추가 하거나 제거 하려면 **열 옵션**를 클릭 합니다.

- 현재 솔루션에 적용 되지 않는 규칙을 숨기려면 **현재 솔루션에 적용 되지 않는 규칙을 숨깁니다**.

- 오류 동작에 할당 된 규칙 표시 및 숨기기를 전환 하려면 **코드 분석 오류를 생성할 수 있는 규칙 표시**를 클릭 합니다.

- 경고 작업에 할당 된 규칙 표시/숨기기를 전환 하려면 **코드 분석 경고를 생성할 수 있는 규칙 표시**를 클릭 합니다.

- **없음** 작업에 할당 된 규칙 표시/숨기기를 전환 하려면 **사용 하도록 설정 되지 않은 규칙 표시**를 클릭 합니다.

- 현재 규칙 집합에 Microsoft 기본 규칙 집합을 추가 하거나 제거 하려면 **자식 규칙 집합 추가 또는 제거**를 클릭 합니다.

## <a name="see-also"></a>관련 항목
 [방법: 관리 코드에 대 한 코드 분석 구성 프로젝트](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md) [코드 분석 규칙 집합 참조](../code-quality/code-analysis-rule-set-reference.md)

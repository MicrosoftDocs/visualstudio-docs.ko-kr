---
title: 규칙 집합 편집기 대화 상자 (레거시) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8010bbbc38dee980ebe89dc60ccb513379103a26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75846322"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>규칙 집합 편집기 대화 상자(레거시)
이 항목에서는 레거시에서 **규칙 집합 편집기** 대화 상자를 사용 하는 방법에 대해 설명 합니다 [!INCLUDE[wfd1](../includes/wfd1-md.md)] . 레거시 [!INCLUDE[wfd2](../includes/wfd2-md.md)]는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 해야 하는 경우에 사용합니다.

 **규칙 집합 편집기** 대화 상자는 rules 파일로 serialize 되는 [policyactivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) 규칙 집합을 만들고 수정 하는 데 사용 됩니다.

> [!NOTE]
> **인코딩을 사용 하 여 XML 편집기**를 사용 하 여. rules 파일을 열려면 먼저 워크플로 또는 활동에 대해 연결 된 디자이너 창을 닫아야 합니다.

 **규칙 집합 편집기** 대화 상자에 액세스 하는 방법에 대 한 자세한 내용은 [방법: Policyactivity 규칙 집합 만들기 (레거시)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)를 참조 하세요.

> [!WARNING]
> [!INCLUDE[wfd2](../includes/wfd2-md.md)] 또는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)]를 대상으로 하는 데 사용되는 레거시 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]의 규칙 편집기는 멀티 타게팅을 지원하지 않습니다.

 다음 표에서는 **규칙 집합 편집기** 대화 상자의 UI (사용자 인터페이스) 요소에 대해 설명 합니다.

|UI 요소|설명|
|----------------|-----------------|
|**규칙 추가**|규칙 집합에 새 규칙 정의를 추가합니다.|
|**Delete**|선택한 규칙을 규칙 집합에서 삭제합니다.|
|**체이닝**|규칙 집합에 사용할 전방 연결의 형식을 지정합니다. 사용 가능한 옵션은 다음과 같습니다.<br /><br /> -   모든 전방 연결 메커니즘을 사용 하도록 지정 하는 **전체**연결 (암시적, 메서드 특성 지정 및 **Update** 함수를 사용 하는 명시적).<br />-   **순차**-전달 체인을 사용 하지 않도록 지정 합니다.<br />-   **명시적 업데이트만**- **업데이트** 작업에 대해서만 전방 연결을 수행 하도록 지정 합니다.<br /><br /> 전방 연결에 대 한 자세한 내용은 [PolicyActivity 활동 사용](https://msdn2.microsoft.com/library/bb675229.aspx)을 참조 하세요.|
|**이름**|규칙 집합 목록 열 머리글입니다. 규칙 목록을 이름별로 정렬하려면 클릭합니다.|
|**우선 순위**|규칙 집합 목록 열 머리글입니다. 규칙 목록을 우선 순위별로 정렬하려면 클릭합니다.|
|**평가할**|규칙 집합 목록 열 머리글입니다. 규칙 목록을 재계산 형식별로 정렬하려면 클릭합니다.|
|**규칙 미리 보기**|규칙 집합 목록 열 머리글입니다. 규칙 목록을 규칙의 조건 및 작업 미리 보기별로 정렬하려면 클릭합니다.|
|**이름:**|규칙의 이름을 입력합니다.|
|**Priority**|규칙의 우선 순위를 입력합니다. 기본 우선 순위는 0입니다.|
|**재계산:**|규칙에 사용할 규칙 재계산의 형식을 지정합니다. 사용 가능한 옵션은 다음과 같습니다.<br /><br /> -   **항상**(필요에 따라 규칙을 다시 평가 하는 경우)<br />-   **Never**로 설정 하면 규칙을 다시 평가 하지 않습니다. 이 경우에는 규칙이 한 번만 실행됩니다.|
|**활성**|규칙을 활성화하려면 선택합니다.|
|**조건**|규칙 조건을 위한 식을 입력합니다. 식 구문에 대한 자세한 내용은 이 페이지의 "조건 및 작업 식 입력" 단원을 참조하세요.|
|**ThenActions:**|Then 작업을 위한 식을 입력합니다. 식 구문에 대한 자세한 내용은 이 페이지의 "조건 및 작업 식 입력" 단원을 참조하세요.|
|**Else 작업:**|Else 작업을 위한 식을 입력합니다. 식 구문에 대한 자세한 내용은 이 페이지의 "조건 및 작업 식 입력" 단원을 참조하세요.|
|**확인**|규칙 집합을 .rules 파일로 저장하려면 클릭합니다.|

 규칙 집합에 대 한 자세한 내용은 [PolicyActivity 활동 사용](https://msdn2.microsoft.com/library/bb675229.aspx)을 참조 하세요.

## <a name="entering-condition-and-action-expressions"></a>조건 및 작업 식 입력
 조건에 대 한 식과 Then 및 Else 작업을 **규칙 집합 편집기** 대화 상자의 해당 텍스트 상자에 텍스트로 입력 합니다. 이를 입력할 수 있습니다 **.** 편집기에서 IntelliSense 형식의 메뉴를 사용 하 여 워크플로에 사용 된 필드, 속성 및 메서드를 참조 합니다. 또는 워크플로 멤버 이름을 직접 입력할 수도 있습니다. 클래스 이름 다음에 메서드 이름을 입력하여 정적 메서드를 참조 형식으로 호출할 수 있습니다.

 AND, OR, NOT 등의 논리 연산자를 조건에 추가할 수 있습니다. 조건자를 추가할 수도 있습니다. 조건자는 이항 연산자 한 개와 피연산자 두 개로 이루어집니다. 지원 되는 이항 연산자는 = =, >, \<, > = 및 <=입니다. 지원되는 피연산자는 상수 값, 산술 함수 및 범위 Public 멤버입니다.

 비교 유형을 지정 하 고 **null** 또는 빈 문자열과 비교할 수 있습니다. `this.Address.State == "WA"`와 같이 복합 형식을 포함하는 변수에서 멤버 호출을 중첩시킬 수 있습니다.

 식은 다음과 같은 연산자를 지원합니다.

- 관계형 연산자: ==, =, !=

- 비교 연산자: <, \<=, > , >=

- 산술 연산자: +, - , *, /, MOD

- 논리 연산자: AND,  &&, OR,  &#124;&#124;, NOT,!

- 비트 연산자: &, &#124;

  식 연산자 우선 순위는 C# 연산자 우선 순위 규칙을 따릅니다.

  조건에 대 한 자세한 내용은 [워크플로에서 조건 사용](https://msdn.microsoft.com/541211f5-d382-4810-894f-71f00b34fa77)을 참조 하세요.

### <a name="halt-and-update-functions"></a>Halt 및 Update 함수
 **Then 작업:** 및 **Else 작업:** 식은 **중지** 및 **업데이트** 함수를 지원 합니다. **중지** 함수를 사용 하려면 **다음 작업** 에 **중지** 를 입력 하거나 **Else action** : 텍스트 상자를 입력 합니다. **중지** 작업을 수행 하면 규칙 집합 실행이 즉시 중지 되 고 호출 코드로 제어가 반환 됩니다. **업데이트** 함수를 전방 연결에 사용 합니다.

 **업데이트** 문은 편집기에서 다음 두 폼 중 하나로 표시 될 수 있습니다. 다음 예제에서는 두 가지 형태를 모두 보여 줍니다.

```
Update(this.Address.State)
Update("this/Address/State")
```

 전방 연결에 **Update** 를 사용 하는 방법에 대 한 자세한 내용은 [Policyactivity 활동 사용](https://msdn2.microsoft.com/library/bb675229.aspx)을 참조 하세요.

## <a name="see-also"></a>관련 항목
 [Policyactivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) [워크플로에서 조건을 사용 하](https://msdn2.microsoft.com/library/bb628447.aspx) 여 [policyactivity 활동을 사용 하 여](https://msdn2.microsoft.com/library/bb675229.aspx) [규칙 집합 선택 대화 상자 (레거시)](../workflow-designer/select-rule-set-dialog-box-legacy.md)

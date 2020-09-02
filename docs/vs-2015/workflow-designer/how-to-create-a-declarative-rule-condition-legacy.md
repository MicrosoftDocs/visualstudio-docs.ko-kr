---
title: '방법: 선언적 규칙 조건 만들기 (레거시) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0c23fed64d7f3a7681fce96663262f6d633299a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75849332"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>방법: 선언적 규칙 조건 만들기(레거시)
이 항목에서는 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 또는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)]를 대상으로 하는 레거시 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 사용하여 규칙 조건을 선언하는 방법에 대해 설명합니다.

 조건문이 **True** 또는 **False**로 평가 됩니다. 선언적 규칙 조건은 [규칙 조건 편집기 대화 상자 (레거시)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) 를 사용 하 여 만들고 워크플로와 함께 XML로 저장 되는 조건 문입니다. 여러 조건자를 결합하는 부울 대수와 워크플로 상태를 비교하는 조건자가 포함될 수 있습니다.

 선언적 규칙 조건은 기본적으로 제공되는 다음과 같은 Windows Workflow Foundation 활동에 사용됩니다.

- [ConditionedActivityGroup 클래스](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx)

- [IfElseBranchActivity (영문 페이지일 수 있음)](https://msdn2.microsoft.com/library/system.workflow.activities.ifelsebranchactivity.aspx)

- [ReplicatorActivity (영문 페이지일 수 있음)](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx)

- [WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx)

- [SequentialWorkflowActivity (영문 페이지일 수 있음)](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx)

- [StateMachineWorkflowActivity (영문 페이지일 수 있음)](https://msdn2.microsoft.com/library/system.workflow.activities.statemachineworkflowactivity.aspx)

### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>규칙 조건 편집기를 사용하여 선언적 규칙 조건을 만들려면

1. 활동의 **속성** 창에서 활동에 따라 **Condition** 속성 또는 **UntilCondition** 속성을 클릭 합니다.

2. 속성의 목록에서 **선언적 규칙 조건** 을 선택 합니다.

3. **Condition** 또는 **UntilCondition** 속성을 확장 합니다.

4. **ConditionName** 속성을 클릭 합니다.

5. **ConditionName** 줄임표 **[...]** 를 클릭 하 여 **조건 선택** 대화 상자를 엽니다.

6. **새 조건** 을 클릭 하 여 **규칙 조건 편집기** 대화 상자를 엽니다.

7. **조건 텍스트 상자** 에 조건에 대 한 식을 입력 합니다.

     조건 식을 만드는 방법에 대 한 자세한 내용은 [규칙 조건 편집기 대화 상자 (레거시)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)를 참조 하세요.

8. 조건 식을 만든 후 **확인** 을 클릭 하 여 대화 상자를 닫고 할당 된 이름의 규칙 조건을 만듭니다.

     **조건 선택** 대화 상자가 열립니다.

     **조건 선택** 대화 상자를 사용 하는 방법에 대 한 자세한 내용은 [조건 선택 대화 상자 (레거시)](../workflow-designer/select-condition-dialog-box-legacy.md)를 참조 하세요.

## <a name="see-also"></a>관련 항목
 [ConditionedActivityGroup를](https://msdn2.microsoft.com/library/bb675237.aspx) 사용 하 여 [IfElseBranchActivity 활동](https://msdn2.microsoft.com/library/bb628465.aspx) [을 사용](https://msdn2.microsoft.com/library/bb628544.aspx) 하는 [레거시 워크플로 활동](../workflow-designer/legacy-workflow-activities.md) 사용 [While 활동](https://msdn2.microsoft.com/library/bb628552.aspx) [규칙 조건 편집기 대화 상자 (레거시)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) [조건 선택 대화 상자 (레거시)](../workflow-designer/select-condition-dialog-box-legacy.md) [워크플로에서 조건 사용](https://msdn2.microsoft.com/library/bb628447.aspx)

---
title: '방법: PolicyActivity 규칙 집합 만들기 (레거시) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0f8599348d204d149f3e28d17d681941ddf476b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75849324"
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>방법: PolicyActivity 규칙 집합 만들기(레거시)
이 항목에서는 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 또는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)]를 대상으로 하는 레거시 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 사용하여 정책 활동 규칙 집합을 만드는 방법에 대해 설명합니다.

 **도구 상자** 에서 워크플로 디자인 화면으로 **정책** 활동 항목을 끌어 온 후에는 [policyactivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) 활동에 대 한 기존 규칙을 선택 하거나 새 규칙 집합을 만들 수 있습니다. 규칙 집합 [선택 대화 상자 (레거시)](../workflow-designer/select-rule-set-dialog-box-legacy.md) 를 사용 하 여 기존 규칙 집합을 선택 하 고 규칙 [집합 편집기 대화 상자 (레거시)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)를 사용 하 여 규칙 집합을 만듭니다.

> [!NOTE]
> 워크플로 디자인 화면에 있는 [Policyactivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) 활동을 두 번 클릭 하 여 [규칙 집합 편집기 대화 상자 (레거시)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) 대화 상자를 직접 열 수 있습니다.

### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>PolicyActivity 활동의 규칙 집합을 선택하거나 만들려면

1. [Policyactivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx)를 마우스 오른쪽 단추로 클릭 한 다음 **속성** 을 클릭 하 여 **속성** 창을 엽니다.

2. **Rulesetreference** 속성을 클릭 합니다.

3. 다음 중 하나를 수행합니다.

    - **Rulesetreference** 줄임표 **[...]** 를 클릭 한 다음, [규칙 집합 선택 대화 상자 (레거시)](../workflow-designer/select-rule-set-dialog-box-legacy.md)에서 기존 규칙 집합을 선택 합니다. 10단계로 이동합니다.

         또는

    - 규칙 집합의 이름을 입력합니다. **Rulesetreference** 줄임표 **[...]** 를 클릭 한 다음, [규칙 집합 선택 대화 상자 (레거시)](../workflow-designer/select-rule-set-dialog-box-legacy.md)에서 **편집** 을 선택 합니다.

         또는

    - 규칙 집합의 이름을 입력합니다. **Rulesetreference** 속성을 확장 하 고 **규칙 집합 정의** 속성에서 줄임표 **[...]** 를 선택 합니다.

         [규칙 집합 편집기 대화 상자 (레거시)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) 가 열립니다.

4. 규칙 [집합 편집기 대화 상자 (레거시)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)에서 규칙 **추가** 를 클릭 하 여 규칙 집합에 새 규칙을 추가 합니다.

5. **이름**, **우선 순위**및 **재평가** 속성을 입력 하거나 기본값을 유지 합니다.

6. **조건**에 대 한 텍스트를 입력 합니다.

7. **Then 작업** 및 **Else 동작**에 대 한 텍스트를 입력 합니다.

8. **규칙 추가** 를 다시 클릭 하 여 다른 규칙을 추가 합니다.

9. 작업을 마쳤으면 **확인**을 클릭합니다.

## <a name="see-also"></a>관련 항목
 [Policyactivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) 정책 활동 [레거시 워크플로 활동](../workflow-designer/legacy-workflow-activities.md) [을 사용 하 여](https://msdn2.microsoft.com/library/bb675229.aspx) [규칙 집합 선택 대화 상자 (](../workflow-designer/select-rule-set-dialog-box-legacy.md) 레거시) [규칙 집합 편집기 대화 상자 (레거시)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)

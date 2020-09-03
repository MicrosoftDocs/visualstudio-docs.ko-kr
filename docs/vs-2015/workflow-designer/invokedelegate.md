---
title: InvokeDelegate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc35aec714255b467431488936605fb37009db9d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659012"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate** 디자이너는 활동을 만들고 구성 하는 데 사용 됩니다 <xref:System.Activities.Statements.InvokeDelegate> .

## <a name="the-invokedelegate-activity"></a>InvokeDelegate 활동

<xref:System.Activities.Statements.InvokeDelegate>는 public 대리자를 호출합니다.

### <a name="using-the-invokedelegate-activity-designer"></a>InvokeDelegate 활동 디자이너 사용

**InvokeDelegate** 활동 디자이너 **는 도구 상자**의 **기본 형식** 범주에 있습니다 .이 범주에 액세스 하려면 도구 **상자** 탭을 클릭 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 하거나, **보기** 메뉴에서 **도구 모음** 을 선택 하거나, ctrl + ALT + X를 선택 합니다.

**InvokeDelegate** 활동 디자이너를 **도구 상자** 에서 끌어다가 등 일반적으로 활동을 배치 하는 화면에 놓을 수 있습니다 [!INCLUDE[wfd2](../includes/wfd2-md.md)] <xref:System.Activities.Statements.Sequence> . 그러면 기본 <xref:System.Activities.Statements.InvokeDelegate>인 InvokeDelegate라는 이름의 <xref:System.Activities.Activity.DisplayName%2A> 활동이 만들어집니다. <xref:System.Activities.Activity.DisplayName%2A> **InvokeDelegate** 활동 디자이너의 머리글 또는 속성 표의 **DisplayName** 상자에서을 편집할 수 있습니다.

### <a name="the-invokedelegate-properties"></a>InvokeDelegate 속성

다음 표에서는 <xref:System.Activities.Statements.InvokeDelegate> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표에서 편집할 수 있으며 일부 속성은 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필수|사용량|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.InvokeDelegate> 활동의 이름입니다. 기본값은 InvokeDelegate입니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|작업이 실행될 때 호출할 <xref:System.Activities.ActivityDelegate>의 이름입니다. 이 속성은 디자이너 화면에서 편집할 수 있습니다. 이 속성은 필수 속성입니다.|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|호출한 대리자의 인수 컬렉션입니다. 키는 <xref:System.Activities.DelegateArgument>에 대한 <xref:System.Activities.ActivityDelegate> 개체의 이름이고 값은 식이 평가되고 해당 <xref:System.Activities.DelegateArgument> 개체에 할당되는 인수입니다. 속성 표에서 **DelegateArguments** 필드에 있는 줄임표 단추를 클릭 하 여이 속성을 설정할 수 있는 **DelegateArguments** 대화 상자를 표시 합니다. 인수 **만들기** 필드를 클릭 하 여 인수를 추가 합니다.|

## <a name="see-also"></a>추가 정보

- [방법: 워크플로 디자이너에서 활동 대리자 정의 및 사용](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)
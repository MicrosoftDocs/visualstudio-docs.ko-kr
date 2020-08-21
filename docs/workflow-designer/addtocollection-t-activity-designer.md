---
title: 워크플로 디자이너-기능 컬렉션 &lt; T &gt; 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ffa24dce2691f061c5947e15d7fc7923d632b38
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88706544"
---
# <a name="addtocollectiont-activity-designer"></a>AddToCollection\<T> 활동 디자이너

작업을 만들고 구성 하는 데 사용 되는 경우에는가 나 **컬렉션 \<T> ** 활동 디자이너가 사용 됩니다 <xref:System.Activities.Statements.AddToCollection%601> .

## <a name="the-addtocollectiont-activity"></a>\<T>작업 컬렉션 작업

<xref:System.Activities.Statements.AddToCollection%601> 활동은 컬렉션에 항목을 추가합니다.

### <a name="using-the-addtocollectiont-activity-designer"></a>\<T>작업 모음 활동 디자이너 사용

**도구 상자**의 **컬렉션** 범주에 있는 작업 도구 모음에서 워크플로 디자이너의 **도구 상자** 탭을 클릭 하 여 액세스할 수 있습니다. ** \<T> ** 또는 **보기** 메뉴에서 **도구 상자** 를 선택 하거나 **ctrl** + **Alt** + **X**를 누릅니다.

**도구 상자** 의 활동 디자이너를 도구 상자에서 끌어와 같이 활동을 배치 하는 워크플로 디자이너 화면에 놓을 수 있습니다. ** \<T> ** <xref:System.Activities.Statements.Sequence> 작업 **컬렉션 \<T> ** 활동 디자이너를 삭제 하면 <xref:System.Activities.Statements.AddToCollection%601> 기본값은 기본값 (기본값)이<인 작업을 만듭니다 <xref:System.Activities.Activity.DisplayName%2A> \> . 기본적으로 *Typeargument* 는 **Int32**입니다. TypeArgument는 속성 표에서 변경할 수 있습니다. <xref:System.Activities.Activity.DisplayName%2A>값은 **<\> T** 활동 디자이너의 머리글 또는 속성 표의 **DisplayName** 상자에서 편집할 수 있습니다. 다른 속성은 속성 표에서 편집해야 합니다.

### <a name="the-addtocollectiont-properties"></a>방법 컬렉션 \<T> 속성

다음 표에서는 <xref:System.Activities.Statements.AddToCollection%601> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다.

|속성 이름|필수|사용|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|거짓|<xref:System.Activities.Statements.AddToCollection%601> 활동의 이름입니다. 기본값은<(기본값) 컬렉션 (Int32)입니다 \> . <xref:System.Activities.Activity.DisplayName%2A> 값은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|컬렉션에 추가할 항목 \<T> 입니다. 이 항목은 유형 *T*이며 *typeargument*유형입니다. 이 항목을 지정하려면 속성 표에 Visual Basic 식을 입력합니다.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|항목이 추가될 컬렉션입니다. 이 컬렉션은 **ICollection<TypeArgument \> **유형입니다. 컬렉션을 지정하려면 속성 표에 Visual Basic 식을 입력합니다.|
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601>에 포함된 항목의 형식 T입니다. 기본적으로이 형식 *인수* 형식은 **Int32**로 설정 됩니다. 형식을 변경 하려면 속성 표의 콤보 상자에서 *Typeargument* 의 값을 변경 합니다.|

## <a name="see-also"></a>참고 항목

- [컬렉션](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T> 활동 디자이너](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)

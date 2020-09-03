---
title: 워크플로 디자이너-ClearCollection &lt; T &gt; 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 710e221441736ecb2415aec32c7f0bfb9a2d99ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88711627"
---
# <a name="clearcollectiont-activity-designer"></a>ClearCollection\<T> 활동 디자이너

**Clearcollection \<T> ** 활동 디자이너는 활동을 만들고 구성 하는 데 사용 됩니다 <xref:System.Activities.Statements.ClearCollection%601> .

## <a name="the-clearcollectiont-activity"></a>ClearCollection \<T> 활동

<xref:System.Activities.Statements.ClearCollection%601> 활동은 모든 항목의 지정한 컬렉션을 지웁니다.

### <a name="using-the-clearcollectiont-activity-designer"></a>ClearCollection \<T> 활동 디자이너 사용

**Clearcollection \<T> ** 활동 디자이너는 **도구**상자의 **컬렉션** 범주에 있습니다 .이 범주에 액세스 하려면 워크플로 디자이너의 **도구 상자** 탭을 클릭 합니다. 또는 **보기** 메뉴에서 **도구 상자** 를 선택 하거나 **ctrl** + **Alt** + **X**를 누릅니다.

**Clearcollection \<T> ** 활동 디자이너를 **도구 상자** 에서 끌어다와 같이 활동을 배치 하는 워크플로 디자이너 화면에 놓을 수 있습니다 <xref:System.Activities.Statements.Sequence> . 활동 디자이너를 삭제 하면 <xref:System.Activities.Statements.ClearCollection%601> 기본값인 <xref:System.Activities.Activity.DisplayName%2A> clearcollection<Int32로 작업을 만듭니다 \> . 기본적으로 *Typeargument* 는 **Int32**입니다. TypeArgument는 속성 표에서 변경할 수 있습니다. <xref:System.Activities.Activity.DisplayName%2A> **Clearcollection<T \> ** 활동 디자이너의 머리글 또는 속성 표의 **DisplayName** 상자에서 값을 편집할 수 있습니다. 다른 속성은 속성 표에서 편집해야 합니다.

### <a name="the-clearcollectiont-properties"></a>ClearCollection \<T> 속성

다음 표에서는 <xref:System.Activities.Statements.ClearCollection%601> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다.

|속성 이름|필수|사용량|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.ClearCollection%601> 활동의 선택적 이름을 지정합니다. 기본값은<Int32의 ClearCollection입니다 \> . <xref:System.Activities.Activity.DisplayName%2A> 값은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|선언할 항목 컬렉션을 지정합니다. 이 컬렉션은 ICollection 유형 **입니다 \<TypeArgument> .** 컬렉션을 지정하려면 속성 표에 Visual Basic 식을 입력합니다.|
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601>에 포함된 T 형식의 항목을 지정합니다. 기본적으로이 형식 *인수* 형식은 **Int32**로 설정 됩니다. 형식을 변경 하려면 속성 표의 콤보 상자에서 *Typeargument* 의 값을 변경 합니다.|

## <a name="see-also"></a>추가 정보

- [컬렉션](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
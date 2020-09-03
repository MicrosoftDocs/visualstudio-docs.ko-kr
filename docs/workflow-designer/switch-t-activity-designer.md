---
title: 워크플로 디자이너-Switch &lt; T &gt; 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7430dec75e898a6695b146ce50076b8f57ed9d3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88711614"
---
# <a name="switcht-activity-designer"></a>Switch\<T> 활동 디자이너

<xref:System.Activities.Statements.Switch%601> 활동은 지정된 식을 계산하고 연관된 키가 계산에서 얻은 값과 일치하는 활동 컬렉션의 활동을 실행합니다.

**스위치<T \> ** 활동 디자이너는 <xref:System.Activities.Statements.Switch%601> 워크플로 디자이너에서 활동을 만들고 구성 하는 데 사용 됩니다.

## <a name="the-switchtactivity"></a>전환 \<T> 작업

<xref:System.Activities.Statements.Switch%601> 활동에는 <xref:System.Activities.Statements.Switch%601.Expression%2A> 및 <xref:System.Activities.Statements.Switch%601.Cases%2A> 사전이 포함되어 있습니다. 사전의 각 사례는 *키* 와 해당 *값*으로 사용 되는 활동을 포함 하는 쌍으로 구성 됩니다. <xref:System.Activities.Statements.Switch%601> 활동은 <xref:System.Activities.Statements.Switch%601.Expression%2A>을 계산한 후 각 키와 비교하고, 일치 하는 항목이 있으면 해당 활동이 실행 됩니다. 사전 키는 사전의 같음 비교자로 정의된 같음 형식에 따라 고유해야 하므로 일치하는 항목은 하나만 존재할 수 있습니다. 일치하는 항목이 없으면 <xref:System.Activities.Statements.Switch%601.Default%2A> 활동이 실행됩니다.

## <a name="how-to-use-the-switcht-activity-designer"></a>Switch 활동 디자이너를 사용 하는 방법 \<T>

**도구 상자**의 **제어 흐름** 범주에 있는 ** \<T> Switch** 활동 디자이너에 액세스 합니다. 사용자가 활동에 사용 된 제네릭 형식 *T* 를 지정할 수 있도록 하는 워크플로 디자이너 **형식 선택** 대화 상자를 표시 합니다 <xref:System.Activities.Statements.Switch%601> . 기본값은 **Int32**입니다. 제네릭 형식 *t* 를 선택 하면 **Switch<t \> ** 디자이너가 workflow designer에 추가 됩니다.

다음은 **스위치<T \> ** 디자이너의 속성입니다. 이러한 모든 속성을 속성 표에서 편집할 수 있습니다. 일부 속성은 디자이너 화면에서도 편집할 수 있습니다.

다음 표에서는 가장 유용한 <xref:System.Activities.Statements.Switch%601> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다.

|속성 이름|필수|사용량|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Switch%601> 활동 디자이너의 이름을 지정합니다. 기본값은 스위치<Int32 \> 입니다. **속성** 창에서 또는 디자이너 헤더에서 직접 값을 편집할 수 있습니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|실행할 case를 결정하기 위해 case 컬렉션의 키와 비교하는 데 사용할 식을 지정합니다.|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||일치하는 항목이 없는 경우에 실행할 활동을 지정합니다. 디자이너에서 **작업 추가** 단추를 클릭 하 여 활동을 삭제할 수 있는 **기본** 상자를 엽니다.|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||계산할 case를 지정합니다. 사례를 추가 하려면 **Switch \<T> ** designer 아래쪽의 **새 사례 추가** 단추를 클릭 합니다. 단추는 textbox (스위치를 추가할 때 선택한 제네릭 형식이 \<T> 문자열 또는 Enum 인 경우 콤보 상자)로 바뀝니다. Case **값** 상자에 키를 추가한 후 사례 영역이 확장 되 고 해당 사례에 대 한 실행 논리를 정의 하기 위해 "여기에 작업 놓기" 힌트 텍스트가 있는 작업을 삭제할 수 있습니다.|

case 키가 중복되지 않는 한 여러 case를 추가할 수 있습니다. 키가 중복되는 경우 지정한 case 키가 이미 있으며 다른 키를 선택해야 한다는 메시지가 표시된 오류 대화 상자가 나타납니다. **스위치 \<T> ** 디자이너에서 한 번에 하나의 사례 영역만 확장 된 보기에 있을 수 있습니다. case 영역이 축소된 보기로 되어 있는 경우 case 영역을 클릭하면 보기가 확장됩니다. 축소된 case는 디자이너에서 case 내 활동의 표시 이름(있는 경우)이 case 오른쪽에 표시됩니다. 그렇지 않으면 **작업 추가** 단추를 클릭 하 여 대/소문자를 확장 하 고 활동을 추가할 수 있습니다.

기존 case의 키를 클릭하면 키 레이블이 텍스트 상자로 바뀌어 case 키를 편집할 수 있게 됩니다.

case를 삭제하는 방법은 두 가지입니다.

- case를 선택하여 삭제합니다.

- 사례를 선택 하 고 마우스 오른쪽 단추를 클릭 하 여 상황에 맞는 메뉴를 표시 하 고 **삭제**를 선택 합니다.

삭제하려면 case 자체를 선택해야 합니다. case 내의 활동을 선택하여 삭제하는 경우 case가 아닌 활동만 삭제됩니다.

## <a name="see-also"></a>추가 정보

- [제어 흐름](../workflow-designer/control-flow-activity-designers.md)

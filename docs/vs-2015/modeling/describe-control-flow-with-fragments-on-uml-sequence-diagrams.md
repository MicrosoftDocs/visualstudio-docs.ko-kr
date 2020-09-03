---
title: UML 시퀀스 다이어그램의 조각으로 제어 흐름 설명 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.interactionoperand
- vs.teamarch.sequencediagram.combinedfragment
helpviewer_keywords:
- UML sequence diagrams, control flow
- UML sequence diagrams, fragments
- sequence diagrams, fragments
- sequence diagrams, control flow
ms.assetid: efcc0949-be7e-4cf4-99ef-47c36b3803ae
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40f48891107c2eb3250b6b050e00c3650812d386
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669811"
---
# <a name="describe-control-flow-with-fragments-on-uml-sequence-diagrams"></a>UML 시퀀스 다이어그램의 조각으로 제어 흐름을 설명합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML 시퀀스 다이어그램에서 *결합 조각* 을 통해 루프, 분기 및 기타 대체 방법을 표시할 수 있습니다.

 결합 조각은 하나 이상의 *상호 작용 피연산자*로 구성되고 이 상호 작용 피연산자는 각각 하나 이상의 메시지, 사용 작용 사용 또는 결합 조각을 포함합니다.

> [!NOTE]
> 이 항목에서는 시퀀스 다이어그램의 조각에 대해 설명합니다. UML 시퀀스 다이어그램을 읽는 방법에 대 한 자세한 내용은 [Uml 시퀀스 다이어그램: 참조](../modeling/uml-sequence-diagrams-reference.md)를 참조 하세요. UML 시퀀스 다이어그램을 그리는 방법에 대한 자세한 내용은 [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md)을 참조하세요.

 ![두 개의 상호 작용 피연산자가 포함된 결합 조각](../modeling/media/uml-seqfragments.png "UML_SeqFragments")

 그림에 표시된 요소는 다음과 같습니다.

1. 결합 조각. 다양한 결합 조각이 있습니다. 이 예제는 메시지의 대체 시퀀스가 발생할 수 있음을 표시하는 데 사용할 수 있는 대체 결합 조각입니다.

2. 상호 작용 피연산자. 모든 결합 조각은 하나 이상의 상호 작용 피연산자를 포함하고 이 상호 작용 피연산자는 메시지, 상호 작용 사용 및 더 작은 결합 조각을 포함할 수 있습니다. 이 예제에서 대체 결합 조각에는 메시지의 대체 시퀀스를 표시하는 상호 작용 연산 두 개가 있습니다.

3. 내부를 클릭하여 각 상호 작용 피연산자를 개별적으로 선택할 수 있습니다. 이 예제에서는 맨 위 결합 조각이 선택되므로 해당 경계가 표시될 수 있습니다. 일반적으로 상호 작용 피연산자 사이에는 구분선만 표시됩니다.

    > [!NOTE]
    > 맨 위 상호 작용 피연산자를 선택하려면 결합 조각의 맨 위와 너무 가깝게 클릭하면 안 됩니다.

4. 가드. 각 상호 작용 피연산자에 가드를 제공할 수 있습니다. 이는 상호 작용 피연산자 내부에서 메시지가 수행되는 조건을 설명합니다.

## <a name="creating-combined-fragments"></a>결합 조각 만들기
 만들 수 있는 조각 종류 목록은 [결합 조각 종류](#KindsOfFragment)를 참조하세요.

#### <a name="to-create-a-combined-fragment"></a>결합 조각을 만들려면

1. 모두 같은 수명선이나 실행 발생에서 시작되는 한 메시지 또는 일련의 메시지를 선택합니다.

   > [!NOTE]
   > 메시지를 두 개 이상 선택할 경우 메시지가 연속 시퀀스를 구성해야 합니다.

2. 메시지의 하나를 마우스 오른쪽 단추로 클릭하여 **코드 감싸기**를 가리키고 원하는 결합 조각 종류를 클릭합니다(예: **Alt 결합 조각**).

    새 결합 조각이 나타납니다. 제목에는 선택한 결합 조각 종류(예: **Alt**)가 표시됩니다.

    결합 조각 내부에는 선택한 메시지를 포함하는 조각이 있습니다.

   몇몇 결합 조각 종류에는 상호 작용 피연산자를 추가할 수 있습니다.

   결합 조각 내에서 메시지를 다시 정렬한 후 바로 가기 메뉴에서 **레이아웃 다시 정렬** 을 선택하여 결합 조각 프레임의 크기를 조정합니다.

#### <a name="to-add-a-new-interaction-operand-to-a-combined-fragment"></a>결합 조각에 새 상호 작용 피연산자를 추가하려면

1. 상호 작용 피연산자(2) 내부, 포함된 조각 외부 및 결합 조각 제목 아래의 빈 공간을 마우스 오른쪽 단추로 클릭합니다.

2. **추가**를 가리킵니다.

3. **다음 항목 앞에 상호 작용 피연산자**또는 **다음 항목 뒤에 상호 작용 피연산자**를 클릭합니다.

4. 메시지 도구를 사용하거나 기존 메시지를 복사한 후 붙여넣는 방식으로 새 상호 작용 연산자 내부에 메시지를 추가할 수 있습니다.

   내부의 메시지가 실행되는 조건을 설명하도록 상호 작용 연산자의 **가드** 속성을 설정할 수 있습니다. 예를 들어 **루프** 결합 조각에서 가드를 사용하여 루프가 계속되는 조건을 지정할 수 있습니다. **Alt** 결합 조각에서 각 상호 작용 피연산자에 대한 개별 조건을 지정할 수 있습니다.

#### <a name="to-set-the-guard-of-an-interaction-operand"></a>상호 작용 피연산자의 가드를 설정하려면

1. 상호 작용 피연산자(2) 내부, 포함된 조각 외부의 빈 공간을 클릭합니다.

    상호 작용 피연산자 및 가드 조건 주위에 선택 테두리가 나타납니다.

    **속성** 창의 제목에 **상호 작용 피연산자**가 표시됩니다.

2. 가드 조건을 입력합니다.

    조건이 조각(4)의 맨 위 가까이에 표시됩니다.

   몇몇 종류 결합 조각의 속성을 설정할 수 있습니다.

#### <a name="to-set-or-view-the-properties-of-a-combined-fragment"></a>결합 조각의 속성을 설정하거나 보려면

- 결합 조각의 제목을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.

    > [!NOTE]
    > 결합 조각 종류에 따라 다른 속성이 포함됩니다.

## <a name="kinds-of-combined-fragment"></a><a name="KindsOfFragment"></a> 결합 조각의 종류

### <a name="fragments-describing-control-flow"></a>제어 흐름을 설명하는 조각
 단순한 시퀀스 조각에서 하나의 일반적인 시퀀스만 표시합니다. 다음 결합 조각 형식을 사용하여 다양한 상황에서 발생할 수 있는 변형을 설명합니다.

|조각 형식|설명|
|-------------------|-----------------|
|**가입**|선택 사항입니다. 발생하거나 발생하지 않을 수 있는 시퀀스를 포함합니다. 가드에서 조각이 발생할 조건을 지정할 수 있습니다.|
|**#B0**|메시지의 대체 시퀀스를 포함하는 조각 목록이 들어 있습니다. 어떤 상황에서도 하나의 시퀀스만 발생합니다.<br /><br /> 각 조각에 가드를 포함하여 조각이 실행될 수 있는 조건을 지정할 수 있습니다. **else** 가드는 다른 가드가 true가 아닐 경우 실행되어야 하는 조각을 나타냅니다. 모든 가드가 false이고 **else**가 없으면 조각이 실행되지 않습니다.|
|**실행**|조각이 몇 회 반복됩니다. 가드에서 조각이 반복되어야 하는 조건을 지정할 수 있습니다.<br /><br /> 루프 결합 조각에는 조각이 반복될 수 있는 최소 및 최대 횟수를 나타내는 **Min** 및 **Max**속성이 있습니다. 기본값은 제한이 없습니다.|
|**끊어야**|이 조각이 실행되면 나머지 시퀀스가 중단됩니다. 가드를 사용하여 중단이 발생할 조건을 지정할 수 있습니다.|
|**Par**|병렬입니다. 조각의 이벤트가 인터리브될 수 있습니다.|
|**심각**|Par 또는 Seq 조각 내에서 사용됩니다. 이 조각의 메시지가 다른 메시지와 인터리브되지 않아야 함을 나타냅니다.|
|**차이가**|피연산자 조각이 두 개 이상 있습니다. 같은 수명선을 포함하는 메시지는 조각 순서대로 발생해야 합니다. 같은 수명선을 포함하지 않을 경우에는 다른 조각의 메시지가 병렬로 인터리브됩니다.|
|**제품과**|피연산자 조각이 두 개 이상 있습니다. 조각이 지정된 순서대로 발생해야 합니다.|

### <a name="fragments-about-how-to-interpret-the-sequence"></a>시퀀스 해석 방법에 대한 조각
 기본적으로 시퀀스 다이어그램은 발생할 수 있는 일련의 메시지를 나타냅니다. 실행 중인 시스템에서 다이어그램에 표시하도록 선택하지 않은 다른 메시지가 발생할 수 있습니다.

 다음 조각 형식을 사용하여 이 해석을 변경할 수 있습니다.

|조각 형식|설명|
|-------------------|-----------------|
|**고려할**|이 조각이 설명하는 메시지 목록을 지정합니다. 다른 메시지가 실행 중인 시스템에서 발생할 수 있지만 이 설명의 측면에서는 중요하지 않습니다.<br /><br /> **메시지** 속성에 목록을 입력합니다.|
|**무시**|이 조각이 설명하지 않는 메시지 목록입니다. 실행 중인 시스템에서 발생할 수 있지만 이 설명의 측면에서는 중요하지 않습니다.<br /><br /> **메시지** 속성에 목록을 입력합니다.|
|**StartupExpression**|피연산자 조각은 유일한 유효한 시퀀스를 지정합니다. 일반적으로 고려 또는 무시 조각 내에서 사용됩니다.|
|**Neg**|이 조각에 표시된 시퀀스는 발생하면 안 됩니다. 일반적으로 고려 또는 무시 조각 내에서 사용됩니다.|

## <a name="see-also"></a>관련 항목
 [Uml 시퀀스 다이어그램: 지침](../modeling/uml-sequence-diagrams-guidelines.md) [uml 시퀀스 다이어그램: 참조](../modeling/uml-sequence-diagrams-reference.md) [편집 uml 모델 및 다이어그램](../modeling/edit-uml-models-and-diagrams.md)

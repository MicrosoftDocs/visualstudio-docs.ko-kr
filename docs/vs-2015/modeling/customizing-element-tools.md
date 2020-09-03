---
title: 요소 도구 사용자 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b6b35bbb0592f7ec9f8defcd9d78dbba5a6a47a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655018"
---
# <a name="customizing-element-tools"></a>요소 도구 사용자 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

일부 DSL 정의에서는 단일 개념을 요소 그룹으로 나타냅니다. 예를 들어 구성 요소에 고정 된 포트 집합이 있는 모델을 만드는 경우 항상 부모 구성 요소와 동시에 포트를 만들도록 합니다. 따라서 요소를 하나만 포함 하는 것이 아니라 요소 그룹을 만들도록 요소 생성 도구를 사용자 지정 해야 합니다. 이를 위해 요소 생성 도구를 초기화 하는 방법을 사용자 지정할 수 있습니다.

 도구를 다이어그램이 나 요소로 끌어 오면 어떻게 되는지 재정의할 수도 있습니다.

## <a name="customizing-the-content-of-an-element-tool"></a>요소 도구의 콘텐츠 사용자 지정
 각 요소 도구 <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> 는 하나 이상의 모델 요소 및 링크의 serialize 된 버전을 포함 하는 (와)의 인스턴스를 저장 합니다. 기본적으로 요소 도구에는 도구에 대해 지정 하는 클래스의 인스턴스가 하나 포함 되어 있습니다. 원하는 *언어*를 재정의 하 여이를 변경할 수 있습니다 `ToolboxHelper.CreateElementToolPrototype` . 이 메서드는 DSL 패키지가 로드 될 때 호출 됩니다.

 메서드의 매개 변수는 DSL 정의에서 지정한 클래스의 ID입니다. 관심이 있는 클래스를 사용 하 여 메서드를 호출 하는 경우에는 요소를 더 추가할 수 있습니다.

 가 중 p는 주 요소에서 자회사 요소로의 포함 링크를 포함 해야 합니다. 참조 링크를 포함할 수도 있습니다.

 다음 예제에서는 main 요소와 두 개의 포함 된 요소를 만듭니다. 주 클래스를 저항기 라고 하며,이 클래스에는 Terminal 라는 요소에 대 한 두 개의 포함 관계가 있습니다. 포함 역할 속성은 이름이 Terminal1 및 Terminal2이 고 둘 다 복합성이 1.. 1입니다.

```
using Microsoft.VisualStudio.Modeling; ...
public partial class CircuitDiagramToolboxHelper
{
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)
  {
    // A case for each tool to customize:
    if (domainClassId == Resistor.DomainClassId)
    {
      // Set up the prototype elements and links:
      Resistor resistor = new Resistor(store);
      resistor.Terminal1 = new Terminal(store);
      resistor.Terminal2 = new Terminal(store);
      resistor.Terminal1.Name = "T1"; // embedding
      resistor.Terminal2.Name = "T2"; // embedding
      // We could also set up reference links.

      // Create an element group prototype for the toolbox:
      ElementGroup egp = new ElementGroup(store.DefaultPartition);
      egp.AddGraph(resistor, true);
      // We do not have to explicitly include embedded children.
      return egp.CreatePrototype();
    }
    // Element tools for other classes:
    else
      return base.CreateElementToolPrototype(store, domainClassId);
  }
}
```

## <a name="see-also"></a>관련 항목
 [요소 만들기 및 이동 사용자 지정](../modeling/customizing-element-creation-and-movement.md)

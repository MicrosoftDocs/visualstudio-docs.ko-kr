---
title: UML API를 사용 하 여 UML 시퀀스 다이어그램 편집 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML activity diagrams, programming
ms.assetid: 8cdd0203-85ef-4c62-9abc-da4cb26fa504
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cbc7a6ce7edede6759c0562df1e524d932f62b91
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669705"
---
# <a name="edit-uml-sequence-diagrams-by-using-the-uml-api"></a>UML API를 사용하여 UML 시퀀스 다이어그램 편집
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

상호 작용은 수명선 집합 간의 메시지 시퀀스입니다. 상호 작용은 UML 시퀀스 다이어그램에 표시됩니다.

 API에 대 한 자세한 내용은 [VisualStudio](/previous-versions/dd493373(v=vs.140))를 참조 하세요.

 UML 다이어그램에 대 한 명령 및 제스처 처리기를 작성 하는 방법에 대 한 일반적인 소개는 [모델링 다이어그램에서 메뉴 명령 정의](../modeling/define-a-menu-command-on-a-modeling-diagram.md)를 참조 하세요.

## <a name="basic-code"></a>기본 코드

### <a name="namespace-imports"></a>네임스페이스 가져오기
 다음 `using` 문을 포함해야 합니다.

```
using Microsoft.VisualStudio.Uml.Classes;
   // for basic UML types such as IPackage
using Microsoft.VisualStudio.Uml.Interactions;
   // for interaction types
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   // to create elements and use additional functions
```

 메뉴 명령 및 제스처 처리기를 만드는 경우 다음도 필요합니다.

```
using System.ComponentModel.Composition;
   // for Import and Export
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   // for ICommandExtension
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
   // for diagrams and context
```

 자세한 내용은 [모델링 다이어그램에서 메뉴 명령 정의](../modeling/define-a-menu-command-on-a-modeling-diagram.md)를 참조 하세요.

### <a name="getting-the-context"></a>컨텍스트 가져오기
 시퀀스 다이어그램에서 명령 또는 제스처 처리기의 일부로 상호 작용을 편집하는 경우 컨텍스트에 대한 참조를 가져올 수 있습니다. 예를 들면 다음과 같습니다.

```
[SequenceDesignerExtension]
[Export(typeof(ICommandExtension))]
public class MySequenceDiagramCommand : ICommandExtension
{
    [Import]
    public IDiagramContext Context { get; set; }
    public void QueryStatus (IMenuCommand command)
    {
      ISequenceDiagram sequenceDiagram =
          Context.CurrentDiagram as ISequenceDiagram;
         ...
```

### <a name="generated-and-uml-sequence-diagrams"></a>생성된 시퀀스 다이어그램 및 UML 시퀀스 다이어그램
 시퀀스 다이어그램에는 UML 모델링 프로젝트에서 수동으로 만든 다이어그램과 프로그램 코드에서 생성된 다이어그램의 두 종류가 있습니다. `UmlMode` 속성을 사용하여 보유한 시퀀스 다이어그램을 검색합니다.

> [!NOTE]
> 이 속성은 Visual Studio 2013 이전 버전을 사용하여 코드에서 생성된 시퀀스 다이어그램에 대해서만 false를 반환합니다. 여기에는 2013 이전 버전에서 마이그레이션된, 코드에서 생성된 시퀀스 다이어그램이 포함됩니다. 이 버전의 Visual Studio에서는 새 시퀀스 다이어그램 생성을 지원하지 않습니다.

 예를 들어 UML 시퀀스 다이어그램에만 표시되는 메뉴 명령을 만들려는 경우 `QueryStatus()` 메서드에 다음 문을 포함할 수 있습니다.

```
command.Enabled = command.Visible =
      sequenceDiagram != null && sequenceDiagram.UmlMode;
```

 생성된 시퀀스 다이어그램에서 수명선, 메시지 및 기타 요소는 대부분 UML 시퀀스 다이어그램의 경우와 동일합니다. UML 모델에서는 모델 저장소에 다른 모든 요소를 소유하는 모델인 루트가 있습니다. 그러나 생성된 상호 작용은 null 루트를 가진 자체 모델 저장소에 있습니다.

```
IModel rootModel = sequenceDiagram.ModelStore.Root;
    // !sequenceDiagram.UmlMode == (rootModel == null)
```

## <a name="to-create-and-display-an-interaction"></a>상호 작용을 만들고 표시하려면
 패키지 또는 모델의 자식으로 상호 작용을 만듭니다.

 예를 들어 빈 시퀀스 다이어그램에서 수행할 수 있는 명령을 개발하는 경우 항상 상호 작용이 있는지 여부를 먼저 확인해야 합니다.

```
public void Execute (IMenuCommand command)
{
    ISequenceDiagram sequenceDiagram =
         Context.CurrentDiagram as ISequenceDiagram;
    if (sequenceDiagram == null) return;
    // Get the diagram's interaction:
    IInteraction interaction = sequenceDiagram.Interaction;
    // A new sequence diagram might have no interaction:
    if (interaction == null)
    {
       // Get the home package or model of the diagram:
       IPackage parentPackage = sequenceDiagram.GetObject<IPackage>();
       interaction = parentPackage.CreateInteraction();
       // Display the interaction on the sequence diagram:
       sequenceDiagram.Bind(interaction);
    }
```

## <a name="updating-an-interaction-and-its-layout"></a>상호 작용 및 해당 레이아웃 업데이트
 상호 작용을 업데이트하는 경우 항상 다음 메서드 중 하나로 레이아웃을 업데이트하여 작업을 종료합니다.

- `ISequenceDiagram.UpdateShapePositions()` 최근 삽입 또는 이동 된 모양의 위치와 인접 한 모양을 조정 합니다.

- `ISequenceDiagram.Layout([SequenceDiagramLayoutKinds])` 전체 다이어그램을 다시 그립니다. 매개 변수를 사용하여 수명선, 메시지 또는 둘 다의 위치 변경을 지정할 수 있습니다.

  이 기능은 특히 새 요소를 삽입하거나 기존 요소를 이동할 때 중요합니다. 다음 작업 중 하나를 수행할 때까지 다이어그램에서 올바른 위치에 배치되지 않습니다. 일련의 변경을 마쳤을 때 다음 작업 중 하나를 한 번만 호출하면 됩니다.

  명령 후에 실행 취소를 수행하는 사용자가 당황하지 않도록 `ILinkedUndoTransaction`을 사용하여 변경 내용과 최종 `Layout()` 또는 `UpdateShapePositions()` 작업을 묶습니다. 예를 들면 다음과 같습니다.

```
using (ILinkedUndoTransaction transaction = LinkedUndoContext.BeginTransaction("create loop"))
{
  Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop, messages);
  Diagram.UpdateShapePositions();
  transaction.Commit();
}
```

 `ILinkedUndoTransaction`을 사용하려면 클래스에서 다음과 같이 선언해야 합니다.

```
[Import] ILinkedUndoContext LinkedUndoContext { get; set; }
```

 자세한 내용은 [트랜잭션을 사용 하 여 UML 모델 업데이트 링크](../modeling/link-uml-model-updates-by-using-transactions.md)를 참조 하세요.

## <a name="building-an-interaction"></a>상호 작용 빌드

### <a name="to-create-lifelines"></a>수명선을 만들려면

```
ILifeline lifeline = interaction.CreateLifeline();
```

 수명선은 연결 가능 요소, 즉 형식의 인스턴스를 나타냅니다. 예를 들어 상호 작용을 사용하여 구성 요소가 들어오는 메시지를 내부 파트에 위임하는 방식을 표시하는 경우 수명선은 구성 요소의 포트와 파트를 나타낼 수 있습니다.

```
foreach (IConnectableElement part in
            component.Parts
           .Concat<IConnectableElement>(component.OwnedPorts))
{
   ILifeline lifeline = interaction.CreateLifeline();
   lifeline.Represents = part;
}
```

 또는 상호 작용이 임의의 개체 집합을 표시하는 경우 상호 작용 자체에 속성이나 다른 `IConnectableElement`를 만들 수 있습니다.

```
ILifeline lifeline = interaction.CreateLifeline();
IProperty property1 = interaction.CreateProperty();
property1.Type = model.CreateInterface();
property1.Type.Name = "Type 1";
lifeline.Represents = property1;
```

 또 다른 방법으로, 연결 가능 요소에 연결하지 않고 수명선의 이름과 형식을 설정할 수 있습니다.

```
ILifeline lifeline = interaction.CreateLifeline();
lifeline.Name = "c1";
lifeline.SetInstanceType("Customer");
System.Diagnostics.Debug.Assert(
           lifeline.GetDisplayName() == "c1:Customer"  );
```

### <a name="to-create-messages"></a>메시지를 만들려면
 메시지를 만들려면 소스 및 대상 수명선에서 삽입 지점을 식별해야 합니다. 예를 들면 다음과 같습니다.

```
interaction.CreateMessage( sourceInsertionPoint,
                           targetInsertionPoint,
                           MessageKind.Complete,
                           MessageSort.ASynchCall)
```

 소스 또는 대상이 정의되지 않은 메시지를 만들려면

```
interaction.CreateLostFoundMessage(MessageKind.Found, insertionPoint);
```

 수명선의 모든 주요 지점에서 삽입 지점을 식별하는 데 사용할 수 있는 여러 메시지가 있습니다.

|ILifeline의 메서드|이 지점에 삽입하는 데 사용|
|-------------------------|------------------------------------|
|`FindInsertionPointAtTop()`|수명선의 맨 위|
|`FindInsertionPointAtBottom()`|수명선의 맨 아래|
|`FindInsertionPointAfterMessage`<br /><br /> `(IMessage previous)`|지정된 메시지 바로 뒤에 있는 지점|
|`FindInsertionPointAfterExecutionSpecification`<br /><br /> `(IExecutionSpecification previous)`|수명선 또는 부모 실행 사양 블록에 지점이 있을 수 있습니다.|
|`FindInsertionPointAfterInteractionUse`<br /><br /> `(IInteractionUse previous)`|상호 작용 사용 뒤에 있는 지점|
|`FindInsertionPointAfterCombinedFragment`<br /><br /> `(ICombinedFragment previous)`|결합 조각 뒤에 있는 지점|
|`FindInsertionPoint(IExecutionSpecification block)`|실행 블록 맨 위|
|`FindInsertionPoint(IInteractionOperand fragment)`|결합 조각의 피연산자 맨 위|

 메시지를 만들 때 다른 메시지와 교차하는 메시지를 정의하지 않도록 주의하세요.

### <a name="to-create-combined-fragments-and-interaction-uses"></a>결합 조각 및 상호 작용 사용을 만들려면
 요소에서 처리해야 하는 각 수명선의 삽입 지점을 지정하여 결합 조각 및 상호 작용 사용을 만들 수 있습니다. 기존 메시지 또는 조각과 교차하는 지점 집합을 지정하지 않도록 주의하세요.

```
Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop,
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));
Interaction.CreateInteractionUse(
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));
```

 기존 메시지 집합을 처리하는 결합 조각을 만들 수도 있습니다. 메시지는 모두 동일한 수명선 또는 실행 블록에 소싱되어야 합니다.

```
ICombinedFragment cf = Interaction.CreateCombinedFragment(
  InteractionOperatorKind.Loop,
  Interaction.Lifelines.First().GetAllOutgoingMessages());
```

 결합 조각은 항상 하나의 피연산자로 생성됩니다. 새 피연산자를 만들려면 앞이나 뒤에 삽입할 기존 피연산자와 앞 또는 뒤에 삽입할지를 지정해야 합니다.

```
// Create an additional operand before the first
cf.CreateInteractionOperand(cf.Operands.First(), false);
// Create an additional operand after the last:
cf.CreateInteractionOperand(cf.Operands.Last(), true);
```

## <a name="troubleshooting"></a>문제 해결
 변경 작업이 `UpdateShapePositions()` 또는 `Layout()` 작업으로 완료되지 않은 경우 모양이 잘못된 위치에 나타납니다.

 대부분의 다른 문제는 삽입 지점이 잘못 정렬되어 새 메시지 또는 조각이 다른 메시지 또는 조각과 교차하는 경우에 발생합니다. 증상으로, 변경 작업이 수행되지 않거나 예외가 발생할 수 있습니다. `UpdateShapePositions()` 또는 `Layout()` 작업이 수행될 때까지 예외가 발생하지 않을 수도 있습니다.

## <a name="see-also"></a>추가 정보

- [VisualStudio.](/previous-versions/dd493373(v=vs.140))
- [UML 모델 및 다이어그램 확장](../modeling/extend-uml-models-and-diagrams.md)
- [모델링 다이어그램의 메뉴 명령 정의](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
- [사용자 지정 모델링 도구 상자 항목 정의](../modeling/define-a-custom-modeling-toolbox-item.md)
- [UML 모델에 대한 유효성 검사 제약 조건 정의](../modeling/define-validation-constraints-for-uml-models.md)
- [Programming with the UML API](../modeling/programming-with-the-uml-api.md)

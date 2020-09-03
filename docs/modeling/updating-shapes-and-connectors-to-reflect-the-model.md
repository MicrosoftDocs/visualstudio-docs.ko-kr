---
title: 모양 및 연결선을 업데이트하여 모델 반영
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83a43e8570ea65373b8cac0bd3e3e7a8dc1f5791
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76115029"
---
# <a name="update-shapes-and-connectors-to-reflect-the-model"></a>모양 및 연결선을 업데이트하여 모델 반영

Visual Studio의 도메인별 언어에서 기본 모델의 상태를 반영 하는 모양의 모양을 만들 수 있습니다.

이 항목의 코드 예제는 프로젝트의 파일에 추가 해야 합니다 `.cs` `Dsl` . 각 파일에는 다음 지시문이 필요 합니다.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
```

## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>데코레이터 표시 여부를 제어 하는 도형 맵 속성 설정

DSL 정의에서 모양과 도메인 클래스 간의 매핑을 구성 하 여 프로그램 코드를 작성 하지 않고도 데코레이터의 표시 여부를 제어할 수 있습니다. 자세한 내용은 [도메인별 언어를 정의 하는 방법](../modeling/how-to-define-a-domain-specific-language.md)을 참조 하세요.

## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>모양의 색 및 스타일을 속성으로 노출

DSL 정의에서 shape 클래스를 마우스 오른쪽 단추로 클릭 하 고 **노출 추가**를 가리킨 다음 **채우기 색**과 같은 항목 중 하나를 클릭 합니다.

이제 셰이프에는 프로그램 코드 또는 사용자로 설정할 수 있는 도메인 속성이 있습니다. 예를 들어 명령 또는 규칙의 프로그램 코드에서이를 설정 하려면 다음을 작성 합니다.

`shape.FillColor = System.Drawing.Color.Red;`

사용자가 아니라 프로그램 제어 에서만 속성 변수를 만들려는 경우 DSL 정의 다이어그램에서 **채우기 색** 과 같은 새 도메인 속성을 선택 합니다. 그런 다음 속성 창 **에서을 검색 가능으로 설정** `false` 하거나 **UI Readonly** 를로 설정 `true` 합니다.

## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>색, 스타일 또는 위치가 모델 요소 속성에 따라 달라 지도록 변경 규칙 정의
 셰이프가 모델의 다른 부분에 종속 되는 모양을 업데이트 하는 규칙을 정의할 수 있습니다. 예를 들어 모델 요소의 속성에 따라 셰이프의 색을 업데이트 하는 모델 요소에 대 한 변경 규칙을 정의할 수 있습니다. 변경 규칙에 대 한 자세한 내용은 [규칙 변경 내용을 모델 내에서 전파](../modeling/rules-propagate-changes-within-the-model.md)를 참조 하세요.

 실행 취소 명령이 수행 될 때 규칙이 호출 되지 않으므로 저장소 내에서 유지 관리 되는 속성을 업데이트 하는 데만 규칙을 사용 해야 합니다. 여기에는 도형의 크기 및 표시 유형과 같은 일부 그래픽 기능이 포함 되지 않습니다. 셰이프의 이러한 기능을 업데이트 하려면 [비-스토어 그래픽 기능 업데이트](#OnAssociatedProperty)를 참조 하세요.

 다음 예제에서는 `FillColor` 이전 섹션에서 설명한 대로 도메인 속성으로를 노출 했다고 가정 합니다.

```csharp
[RuleOn(typeof(ExampleElement))]
  class ExampleElementPropertyRule : ChangeRule
  {
    public override void ElementPropertyChanged(ElementPropertyChangedEventArgs e)
    {
      base.ElementPropertyChanged(e);
      ExampleElement element = e.ModelElement as ExampleElement;
      // The rule is called for every property that is updated.
      // Therefore, verify which property changed:
      if (e.DomainProperty.Id == ExampleElement.NameDomainPropertyId)
      {
        // There is usually only one shape:
        foreach (PresentationElement pel in PresentationViewsSubject.GetPresentation(element))
        {
          ExampleShape shape = pel as ExampleShape;
          // Replace this with a useful condition:
          shape.FillColor = element.Name.EndsWith("3")
                     ? System.Drawing.Color.Red : System.Drawing.Color.Green;
        }
      }
    }
  }
  // The rule must be registered:
  public partial class OnAssociatedPropertyExptDomainModel
  {
    protected override Type[] GetCustomDomainModelTypes()
    {
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
      types.Add(typeof(ExampleElementPropertyRule));
      // If you add more rules, list them here.
      return types.ToArray();
    }
  }
```

## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>OnChildConfigured 된 셰이프 속성을 사용 하 여 초기화

셰이프를 처음 만들 때 셰이프 속성을 설정 하려면 `OnChildConfigured()` 다이어그램 클래스의 부분 정의에 재정의를 적용 합니다. 다이어그램 클래스는 DSL 정의에 지정 되 고 생성 된 코드는 **Dsl\generated Code\Diagram.cs**에 있습니다. 예를 들면 다음과 같습니다.

```csharp
partial class MyLanguageDiagram
{
  protected override void OnChildConfigured(ShapeElement child, bool childWasPlaced, bool createdDuringViewFixup)
  {
    base.OnChildConfigured(child, childWasPlaced, createdDuringViewFixup);
    ExampleShape shape = child as ExampleShape;
    if (shape != null)
    {
      if (!createdDuringViewFixup) return; // Ignore load from file.
      ExampleElement element = shape.ModelElement as ExampleElement;
      // Replace with a useful condition:
      shape.FillColor = element.Name.EndsWith("3")
          ? System.Drawing.Color.Red : System.Drawing.Color.Green;
    }
    // else deal with other types of shapes and connectors.
  }
}
```

이 메서드는 도메인 속성 및 저장 하지 않는 기능 (예: 모양의 크기)에 모두 사용할 수 있습니다.

## <a name="use-associatevaluewith-to-update-other-features-of-a-shape"></a><a name="OnAssociatedProperty"></a> AssociateValueWith ()를 사용 하 여 모양의 다른 기능 업데이트

연결선의 그림자가 있는지 여부 등 셰이프의 일부 기능에는 기능을 도메인 속성으로 노출 하는 기본 제공 방법이 없습니다.  이러한 기능에 대 한 변경 내용은 트랜잭션 시스템의 제어를 받지 않습니다. 따라서 사용자가 실행 취소 명령을 수행할 때 규칙이 호출 되지 않기 때문에 규칙을 사용 하 여 업데이트 하는 것은 적절 하지 않습니다.

대신를 사용 하 여 이러한 기능을 업데이트할 수 있습니다 <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A> . 다음 예제에서 커넥터의 화살표 스타일은 커넥터에 표시 되는 관계의 도메인 속성 값에 의해 제어 됩니다.

```csharp
public partial class ArrowConnector // My connector class.
{
    /// <summary>
    /// Called whenever a registered property changes in the associated model element.
    /// </summary>
    /// <param name="e"></param>
    protected override void OnAssociatedPropertyChanged(VisualStudio.Modeling.Diagrams.PropertyChangedEventArgs e)
    {
      base.OnAssociatedPropertyChanged(e);
      // Can be called for any property change. Therefore,
      // Verify that this is the property we're interested in:
      if ("IsDirected".Equals(e.PropertyName))
      {
        if (e.NewValue.Equals(true))
        { // Update the shape's built-in Decorator feature:
          this.DecoratorTo = LinkDecorator.DecoratorEmptyArrow;
        }
        else
        {
          this.DecoratorTo = null; // No arrowhead.
        }
      }
    }

    // OnAssociatedPropertyChanged is called only for properties
    // that have been registered using AssociateValueWith().
    // InitializeResources is a convenient place to call this.
    // This method is invoked only once per class, even though
    // it is an instance method.
    protected override void InitializeResources(StyleSet classStyleSet)
    {
      base.InitializeResources(classStyleSet);
      AssociateValueWith(this.Store, Wire.IsDirectedDomainPropertyId);
      // Add other properties here.
    }
}
```

`AssociateValueWith()` 등록 하려는 각 도메인 속성에 대해 한 번 호출 해야 합니다. 호출 된 후에는 지정 된 속성에 대 한 모든 변경 내용이 `OnAssociatedPropertyChanged()` 속성의 모델 요소를 표시 하는 모든 셰이프에서를 호출 합니다.

각 인스턴스에 대해를 호출할 필요는 없습니다 `AssociateValueWith()` . InitializeResources는 인스턴스 메서드 이지만 각 shape 클래스에 대해 한 번만 호출 됩니다.

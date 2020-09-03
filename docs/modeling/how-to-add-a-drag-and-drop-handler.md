---
title: '방법: 끌어서 놓기 처리기 추가'
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9272a530eaa15f902a2e295aeaa6d8b34c4eccdd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545667"
---
# <a name="how-to-add-a-drag-and-drop-handler"></a>방법: 끌어서 놓기 처리기 추가

사용자가 다른 다이어그램이 나 Visual Studio의 다른 부분에서 항목을 다이어그램으로 끌 수 있도록 DSL에 끌어서 놓기 이벤트에 대 한 처리기를 추가할 수 있습니다. 또한 두 번 클릭 등의 이벤트용 처리기도 추가할 수 있습니다. 끌어서 놓기 및 두 번 클릭 처리기를 *제스처 처리기*라고 합니다.

이 항목에서는 다른 다이어그램에서 시작되는 끌어서 놓기 제스처에 대해 설명합니다. 단일 다이어그램 내의 이동 및 복사 이벤트에 대해서는 `ElementOperations`의 서브클래스를 정의하는 방식을 대신 사용할 수 있습니다. 자세한 내용은 [복사 동작 사용자 지정](../modeling/customizing-copy-behavior.md)을 참조 하세요. DSL 정의를 사용자 지정할 수도 있습니다.

## <a name="defining-gesture-handlers-by-overriding-shapeelement-methods"></a>ShapeElement 메서드를 재정의하여 제스처 처리기 정의

`OnDragDrop`, `OnDoubleClick` , `OnDragOver` 및 기타 메서드를 재정의할 수 있습니다.

DSL 프로젝트에 새 코드 파일을 추가합니다. 제스처 처리기의 경우 일반적으로 다음 지시문이 적어도 하나 이상 있어야 합니다 `using` .

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using System.Linq;
```

새 파일에서 끌기 작업에 응답해야 하는 모양 또는 다이어그램 클래스에 대해 partial 클래스를 정의합니다. 이렇게 하려면 다음 메서드를 재정의합니다.

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragOver%2A>-이 메서드는 끌기 작업 중에 마우스 포인터가 셰이프에 들어가면 호출 됩니다. 메서드는 사용자가 끌어 온 항목을 검사한 다음 사용자가 이 모양에 해당 항목을 놓을 수 있는지 여부를 나타내도록 Effect 속성을 설정해야 합니다. Effect 속성은 해당 모양 위에 있는 커서의 모양을 결정하며 사용자가 마우스 단추를 놓을 때 `OnDragDrop()`을 호출할지도 결정합니다.

    ```csharp
    partial class MyShape // MyShape generated from DSL Definition.
    {
        public override void OnDragOver(DiagramDragEventArgs e)
        {
          base.OnDragOver(e);
          if (e.Effect == System.Windows.Forms.DragDropEffects.None
               && IsAcceptableDropItem(e)) // To be defined
          {
            e.Effect = System.Windows.Forms.DragDropEffects.Copy;
          }
        }
    ```

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragDrop%2A> -이 메서드는 이전에가 `OnDragOver(DiagramDragEventArgs e)` `e.Effect` 이외의 값으로 설정 된 경우 마우스 포인터가이 모양 또는 다이어그램 위에 있는 동안 마우스 단추를 놓으면 호출 됩니다 `None` .

    ```csharp
    public override void OnDragDrop(DiagramDragEventArgs e)
    {
          if (!IsAcceptableDropItem(e))
          {
            base.OnDragDrop(e);
          }
          else
          { // Process the dragged item, for example merging a copy into the diagram
            ProcessDragDropItem(e); // To be defined
          }
    }
    ```

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDoubleClick%2A> -이 메서드는 사용자가 모양이 나 다이어그램을 두 번 클릭할 때 호출 됩니다.

     자세한 내용은 [방법: 모양 또는 데코레이터 클릭 가로채기](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)를 참조 하세요.

끌어 온 항목이 적절한지 여부를 확인하도록 `IsAcceptableDropItem(e)`을 정의하고 항목을 놓을 때 모델을 업데이트하도록 ProcessDragDropItem(e)을 정의합니다. 이러한 메서드는 먼저 이벤트 인수에서 항목을 추출해야 합니다. 이 작업을 수행 하는 방법에 대 한 자세한 내용은 [끌어 온 항목에 대 한 참조를 가져오는 방법](#to-send-an-object-from-a-source-dsl)을 참조 하세요.

## <a name="define-gesture-handlers-by-using-mef"></a>MEF를 사용 하 여 제스처 처리기 정의

타사 개발자가 DSL에 대해 고유한 처리기를 정의할 수 있도록 하려면 이 메서드를 사용합니다. 사용자는 DSL을 설치한 후 타사 확장을 설치할 수 있습니다.

MEF(Managed Extensibility Framework)를 사용하면 최소한의 구성으로 설치 가능한 구성 요소를 정의할 수 있습니다. 자세한 내용은 [MEF(관리되는 확장성 프레임워크 개요)](/dotnet/framework/mef/index)를 참조하십시오.

### <a name="to-define-a-mef-gesture-handler"></a>MEF 제스처 처리기를 정의하려면

1. **Dsl** 및 **dslpackage** 프로젝트에 추가 [MEF를 사용 하 여 Dsl 확장](../modeling/extend-your-dsl-by-using-mef.md)에 설명 된 **mefextension** 파일을 추가 합니다.

2. 이제 제스처 처리기를 MEF 구성 요소로 정의할 수 있습니다.

    ```csharp
    // This attribute is defined in the generated file
    // DslPackage\MefExtension\DesignerExtensionMetaDataAttribute.cs:
    [MyDslGestureExtension]
    public class MyGestureHandlerClassName : IGestureExtension
    {
      /// <summary>
      /// Called to determine whether a drag onto the diagram can be accepted.
      /// </summary>
      /// <param name="diagramDragEventArgs">Contains a link to the item that is being dragged</param>
      /// <param name="targetMergeElement">The shape or connector that the mouse is over</param>
      /// <returns>True if the item can be accepted on the targetMergeElement.</returns>
      public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
      {
        MyShape target = targetMergeElement as MyShape;
        if (target == null) return false;
        if (target.IsAcceptableDropItem(diagramDragEventArgs)) return true;
        return false;
      }
      public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
      {
        MyShape target = targetMergeElement as MyShape;
        if (target == null || ! target.IsAcceptableDropItem(diagramDragEventArgs)) return;
        // Process the dragged item, for example merging a copy into the diagram:
        target.ProcessDragDropItem(diagramDragEventArgs);
     }
    ```

     여러 형식의 개체를 끌어 온 등의 경우에는 둘 이상의 제스처 처리기 구성 요소를 만들 수 있습니다.

3. 대상 모양, 연결선 또는 다이어그램 클래스에 대해 partial 클래스 정의를 추가하고 `IsAcceptableDropItem()` 및 `ProcessDragDropItem()` 메서드를 정의합니다. 이러한 메서드는 먼저 이벤트 인수에서 끈 항목을 추출해야 합니다. 자세한 내용은 [끌어 온 항목에 대 한 참조를 가져오는 방법](#to-send-an-object-from-a-source-dsl)을 참조 하세요.

## <a name="how-to-decode-the-dragged-item"></a>끌어 온 항목을 디코딩하는 방법

임의의 창이나 바탕 화면 또는 DSL에서 요소를 끌 수 있습니다.

사용자가 다이어그램으로 항목을 끌거나 다이어그램의 부분 간에 항목을 끌 때는 끌어 놓는 항목에 대한 정보를 `DiagramDragEventArgs`에서 사용할 수 있습니다. 끌기 작업은 화면에 표시된 임의의 개체에서 시작되었을 수 있으므로 다양한 형식 중 하나로 데이터를 사용할 수 있습니다. 코드는 처리 가능한 형식을 인식해야 합니다.

끌기 소스 정보를 사용할 수 있는 형식을 검색하려면 `OnDragOver()` 또는 `CanDragDrop()` 진입 위치에 중단점을 설정하여 디버깅 모드에서 코드를 실행합니다. `DiagramDragEventArgs` 매개 변수의 값을 검사합니다. 정보는 두 가지 형식으로 제공됩니다.

- <xref:System.Windows.Forms.IDataObject>  `Data` -이 속성은 일반적으로 여러 형식으로 된 원본 개체의 serialize 된 버전을 전달 합니다. 이 속성의 가장 유용한 기능은 다음과 같습니다.

  - diagramEventArgs. GetDataFormats ()-끌어온 개체를 디코딩할 수 있는 형식을 나열 합니다. 예를 들어 사용자가 바탕 화면에서 파일을 끄는 경우 사용 가능한 형식에는 파일 이름("`FileNameW`")이 포함됩니다.

  - `diagramEventArgs.Data.GetData(format)` -끌어온 개체를 지정 된 형식으로 디코딩합니다. 적절한 형식으로 개체를 캐스팅합니다. 예를 들면 다음과 같습니다.

    `string fileName = diagramEventArgs.Data.GetData("FileNameW") as string;`

    소스의 모델 버스 참조와 같은 개체를 고유한 사용자 지정 형식으로 전송할 수도 있습니다. 자세한 내용은 [끌어서 놓는 방법으로 모델 버스 참조를 보내는 방법](#to-send-an-object-from-a-source-dsl)을 참조 하세요.

- <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>`Prototype`-사용자가 DSL 또는 UML 모델에서 항목을 끌 수 있도록 하려면이 속성을 사용 합니다. 요소 그룹 프로토타입은 하나 이상의 개체, 링크 및 해당 속성 값을 포함하며 붙여넣기 작업과 도구 상자에서 요소를 추가할 때도 사용됩니다. 프로토타입에서는 개체와 해당 형식을 GUID로 식별합니다. 예를 들어 다음 코드를 사용하면 UML 다이어그램 또는 UML 모델 탐색기에서 클래스 요소를 끌어 놓을 수 있습니다.

    ```csharp
    private bool IsAcceptableDropItem(DiagramDragEventArgs e)
    {
      return e.Prototype != null && e.Prototype.RootProtoElements.Any(element =>
            element.DomainClassId.ToString()
            == "3866d10c-cc4e-438b-b46f-bb24380e1678"); // Accept UML class shapes.
     // Or, from another DSL: SourceNamespace.SourceShapeClass.DomainClassId
    }
    ```

     UML 셰이프를 수락 하려면 실험을 통해 UML 셰이프 클래스의 Guid를 확인 합니다. 일반적으로 모든 다이어그램에는 둘 이상의 요소 형식이 있습니다. 또한 DSL이나 UML 다이어그램에서 끄는 개체는 모델 요소가 아닌 모양입니다.

`DiagramDragEventArgs` 또한에는 현재 마우스 포인터 위치와 사용자가 CTRL, ALT 또는 SHIFT 키를 누르는 지 여부를 나타내는 속성도 있습니다.

## <a name="how-to-get-the-original-of-a-dragged-element"></a>끌어 온 요소의 원본을 가져오는 방법

끌어 온 항목이 DSL 요소이면 소스 모델을 열어 해당 요소에 액세스할 수 있습니다.

이벤트 인수의 `Data` 및 `Prototype` 속성은 끌어 온 모양의 참조만을 포함합니다. 일반적으로는 특정 방식으로 프로토타입에서 파생되는 대상 DSL에 개체를 만들려면 파일 내용을 읽거나 모양이 표시하는 모델 요소로 이동하는 등의 방법으로 원본에 액세스해야 합니다. Visual Studio ModelBus를 사용하면 원본에 액세스할 수 있습니다.

### <a name="to-prepare-a-dsl-project-for-model-bus"></a>ModelBus용 DSL 프로젝트를 준비하려면

Visual Studio 모델 버스에서 원본 DSL에 액세스할 수 있도록 설정 합니다.

1. DSL Designer에서 소스 DSL의 DSL 정의 파일을 엽니다. 디자인 화면을 마우스 오른쪽 단추로 클릭 한 다음 **Modelbus 사용**을 클릭 합니다. 대화 상자에서 옵션 중 하나 또는 둘 다를 선택합니다.  **확인**을 클릭합니다. "ModelBus"라는 새 프로젝트가 DSL 솔루션에 추가됩니다.

2. **모든 템플릿 변환** 을 클릭 하 고 솔루션을 다시 빌드합니다.

### <a name="to-send-an-object-from-a-source-dsl"></a>소스 DSL에서 개체를 보내려면

1. ElementOperations 서브클래스에서 `Copy()`를 재정의하여 MBR(모델 버스 참조)을 IDataObject로 인코딩하도록 지정합니다. 사용자가 소스 다이어그램에서 끌기를 시작하면 이 메서드가 호출됩니다. 그러면 사용자가 대상 다이어그램에 개체를 놓을 때 인코딩된 MBR을 IDataObject에서 사용할 수 있습니다.

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Shell;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Integration;
    using Microsoft.VisualStudio.Modeling.Integration.Shell;
    using System.Drawing; // PointF
    using  System.Collections.Generic; // ICollection
    using System.Windows.Forms; // for IDataObject
    ...
    public class MyElementOperations : DesignSurfaceElementOperations
    {
        public override void Copy(System.Windows.Forms.IDataObject data, System.Collections.Generic.ICollection<ModelElement> elements, ClosureType closureType, System.Drawing.PointF sourcePosition)
        {
          base.Copy(data, elements, closureType, sourcePosition);

          // Get the ModelBus service:
          IModelBus modelBus =
              this.Store.GetService(typeof(SModelBus)) as IModelBus;
          DocData docData = ((VSDiagramView)this.Diagram.ActiveDiagramView).DocData;
          string modelFile = docData.FileName;
          // Get an adapterManager for the target DSL:
          ModelBusAdapterManager manager =
              (modelBus.FindAdapterManagers(modelFile).First());
          ModelBusReference modelReference = manager.CreateReference(modelFile);
          ModelBusReference elementReference = null;
          using (ModelBusAdapter adapter = modelBus.CreateAdapter(modelReference))
          {
            elementReference = adapter.GetElementReference(elements.First());
          }

          data.SetData("ModelBusReference", elementReference);
        }
    ...}
    ```

### <a name="to-receive-a-model-bus-reference-from-a-dsl-in-a-target-dsl-or-uml-project"></a>DSL에서 보낸 모델 버스 참조를 대상 DSL 또는 UML 프로젝트에서 수신하려면

1. 대상 DSL 프로젝트에서 다음 항목에 대한 참조를 추가합니다.

    - 소스 DSL 프로젝트

    - 소스 ModelBus 프로젝트

2. 제스처 처리기 코드 파일에서 다음 네임스페이스 참조를 추가합니다.

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
    using Microsoft.VisualStudio.Modeling.Integration;
    using SourceDslNamespace;
    using SourceDslNamespace.ModelBusAdapters;
    ```

3. 다음 샘플에서는 소스 모델 요소에 액세스하는 방법을 보여줍니다.

    ```csharp
    partial class MyTargetShape // or diagram or connector
    {
      internal void ProcessDragDropItem(DiagramDragEventArgs diagramDragEventArgs)
      {
        // Verify that we're being passed an Object Shape.
        ElementGroupPrototype prototype = diagramDragEventArgs.Prototype;
        if (prototype == null) return;
        if (Company.InstanceDiagrams.ObjectShape.DomainClassId
          != prototype.RootProtoElements.First().DomainClassId)
          return;
        // - This is an ObjectShape.
        // - We need to access the originating Store, find the shape, and get its object.

        IModelBus modelBus = targetDropElement.Store.GetService(typeof(SModelBus)) as IModelBus;

        // Unpack the MBR that was packed in Copy:
        ModelBusReference reference = diagramDragEventArgs.Data.GetData("ModelBusReference") as ModelBusReference;
        using (SourceDslAdapter adapter = modelBus.CreateAdapter(reference) as SourceDslAdapter)
        {
          using (ILinkedUndoTransaction t = LinkedUndoContext.BeginTransaction("doing things"))
          {
            // Quickest way to get the shape from the MBR:
            ObjectShape firstShape = adapter.ResolveElementReference<ObjectShape>(reference);

            // But actually there might be several shapes - so get them from the prototype instead:
            IElementDirectory remoteDirectory = adapter.Store.ElementDirectory;
            foreach (Guid shapeGuid in prototype.SourceRootElementIds)
            {
              PresentationElement pe = remoteDirectory.FindElement(shapeGuid) as PresentationElement;
              if (pe == null) continue;
              SourceElement instance = pe.ModelElement as SourceElement;
              if (instance == null) continue;

              // Do something with the object:
          instance...
            }
            t.Commit();
          }
        }
    }
    ```

### <a name="to-accept-an-element-sourced-from-a-uml-model"></a>UML 모델을 소스로 사용하는 요소를 수락하려면

- 다음 코드 샘플은 UML 다이어그램에서 놓은 개체를 수락합니다.

    ```csharp
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
    using Microsoft.VisualStudio.Uml.Classes;
    using System;
    using System.ComponentModel.Composition;
    using System.Linq;
    ...
    partial class TargetShape
    {
      internal void ProcessDragDropItem(DiagramDragEventArgs diagramDragEventArgs)
      {
            EnvDTE.DTE dte = this.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
            // Find the UML project
            foreach (EnvDTE.Project project in dte.Solution.Projects)
            {
              IModelingProject modelingProject = project as IModelingProject;
              if (modelingProject == null) continue; // not a modeling project
              IModelStore store = modelingProject.Store;
              if (store == null) return;

              foreach (IDiagram dd in store.Diagrams())
              {
                  // Get Modeling.Diagram that implements UML.IDiagram:
                  Diagram diagram = dd.GetObject<Diagram>();

                  foreach (Guid elementId in e.Prototype.SourceRootElementIds)
                  {
                    ShapeElement shape = diagram.Partition.ElementDirectory.FindElement(elementId) as ShapeElement;
                    if (shape == null) continue;
                    // This example assumes the shape is a UML class:
                    IClass classElement = shape.ModelElement as IClass;
                    if (classElement == null) continue;

                    // Now do something with the UML class element ...
                  }
            }
          break; // don't try any more projects
    }  }  }
    ```

## <a name="using-mouse-actions-dragging-compartment-items"></a>마우스 작업 사용: 구획 항목 끌기

셰이프 필드에서 마우스 작업을 가로채는 처리기를 작성할 수 있습니다. 다음 예제에서는 사용자가 마우스로 끌어 구획의 항목을 다시 정렬할 수 있습니다.

이 예제를 빌드하려면 **클래스 다이어그램** 솔루션 템플릿을 사용 하 여 솔루션을 만듭니다. 이때 코드 파일과 다음 코드를 추가하고 네임스페이스를 실제 네임스페이스와 동일하게 조정합니다.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Design;
using Microsoft.VisualStudio.Modeling.Diagrams;
using System.Collections.Generic;
using System.Linq;

// This sample allows users to re-order items in a compartment shape by dragging.

// This example is built on the "Class Diagrams" solution template of VMSDK (DSL Tools).
// You will need to change the following domain class names to your own:
// ClassShape = a compartment shape
// ClassModelElement = the domain class displayed using a ClassShape
// This code assumes that the embedding relationships displayed in the compartments
// don't use inheritance (don't have base or derived domain relationships).

namespace Company.CompartmentDrag  // EDIT.
{
 /// <summary>
 /// Manage the mouse while dragging a compartment item.
 /// </summary>
 public class CompartmentDragMouseAction : MouseAction
 {
  private ModelElement sourceChild;
  private ClassShape sourceShape;
  private RectangleD sourceCompartmentBounds;

  public CompartmentDragMouseAction(ModelElement sourceChildElement, ClassShape sourceParentShape, RectangleD bounds)
   : base (sourceParentShape.Diagram)
  {
   sourceChild = sourceChildElement;
   sourceShape = sourceParentShape;
   sourceCompartmentBounds = bounds; // For cursor.
  }

  /// <summary>
  /// Call back to the source shape to drop the dragged item.
  /// </summary>
  /// <param name="e"></param>
  protected override void OnMouseUp(DiagramMouseEventArgs e)
  {
   base.OnMouseUp(e);
   sourceShape.DoMouseUp(sourceChild, e);
   this.Cancel(e.DiagramClientView);
   e.Handled = true;
  }

  /// <summary>
  /// Ideally, this shouldn't happen. This action should only be active
  /// while the mouse is still pressed. However, it can happen if you
  /// move the mouse rapidly out of the source shape, let go, and then
  /// click somewhere else in the source shape. Yuk.
  /// </summary>
  /// <param name="e"></param>
  protected override void OnMouseDown(DiagramMouseEventArgs e)
  {
   base.OnMouseDown(e);
   this.Cancel(e.DiagramClientView);
   e.Handled = false;
  }

  /// <summary>
  /// Display an appropriate cursor while the drag is in progress:
  /// Up-down arrow if we are inside the original compartment.
  /// No entry if we are elsewhere.
  /// </summary>
  /// <param name="currentCursor"></param>
  /// <param name="diagramClientView"></param>
  /// <param name="mousePosition"></param>
  /// <returns></returns>
  public override System.Windows.Forms.Cursor GetCursor(System.Windows.Forms.Cursor currentCursor, DiagramClientView diagramClientView, PointD mousePosition)
  {
   // If the cursor is inside the original compartment, show up-down cursor.
   return sourceCompartmentBounds.Contains(mousePosition)
    ? System.Windows.Forms.Cursors.SizeNS // Up-down arrow.
    : System.Windows.Forms.Cursors.No;
  }
 }

 /// <summary>
 /// Override some methods of the compartment shape.
 /// *** GenerateDoubleDerived must be set for this shape in DslDefinition.dsl. ****
 /// </summary>
 public partial class ClassShape
 {
  /// <summary>
  /// Model element that is being dragged.
  /// </summary>
  private static ClassModelElement dragStartElement = null;
  /// <summary>
  /// Absolute bounds of the compartment, used to set the cursor.
  /// </summary>
  private static RectangleD compartmentBounds;

  /// <summary>
  /// Attach mouse listeners to the compartments for the shape.
  /// This is called once per compartment shape.
  /// The base method creates the compartments for this shape.
  /// </summary>
  public override void EnsureCompartments()
  {
   base.EnsureCompartments();
   foreach (Compartment compartment in this.NestedChildShapes.OfType<Compartment>())
   {
    compartment.MouseDown += new DiagramMouseEventHandler(compartment_MouseDown);
    compartment.MouseUp += new DiagramMouseEventHandler(compartment_MouseUp);
    compartment.MouseMove += new DiagramMouseEventHandler(compartment_MouseMove);
   }
  }

  /// <summary>
  /// Remember which item the mouse was dragged from.
  /// We don't create an Action immediately, as this would inhibit the
  /// inline text editing feature. Instead, we just remember the details
  /// and will create an Action when/if the mouse moves off this list item.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseDown(object sender, DiagramMouseEventArgs e)
  {
   dragStartElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();
   compartmentBounds = e.HitDiagramItem.Shape.AbsoluteBoundingBox;
  }

  /// <summary>
  /// When the mouse moves away from the initial list item, but still inside the compartment,
  /// create an Action to supervise the cursor and handle subsequent mouse events.
  /// Transfer the details of the initial mouse position to the Action.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseMove(object sender, DiagramMouseEventArgs e)
  {
   if (dragStartElement != null)
   {
    if (dragStartElement != e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault())
    {
     e.DiagramClientView.ActiveMouseAction = new CompartmentDragMouseAction(dragStartElement, this, compartmentBounds);
     dragStartElement = null;
    }
   }
  }

  /// <summary>
  /// User has released the mouse button.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseUp(object sender, DiagramMouseEventArgs e)
  {
    dragStartElement = null;
  }

  /// <summary>
  /// Forget the source item if mouse up occurs outside the
  /// compartment.
  /// </summary>
  /// <param name="e"></param>
  public override void OnMouseUp(DiagramMouseEventArgs e)
  {
   base.OnMouseUp(e);
   dragStartElement = null;
  }

  /// <summary>
  /// Called by the Action when the user releases the mouse.
  /// If we are still on the same compartment but in a different list item,
  /// move the starting item to the position of the current one.
  /// </summary>
  /// <param name="dragFrom"></param>
  /// <param name="e"></param>
  public void DoMouseUp(ModelElement dragFrom, DiagramMouseEventArgs e)
  {
   // Original or "from" item:
   ClassModelElement dragFromElement = dragFrom as ClassModelElement;
   // Current or "to" item:
   ClassModelElement dragToElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();
   if (dragFromElement != null && dragToElement != null)
   {
    // Find the common parent model element, and the relationship links:
    ElementLink parentToLink = GetEmbeddingLink(dragToElement);
    ElementLink parentFromLink = GetEmbeddingLink(dragFromElement);
    if (parentToLink != parentFromLink && parentFromLink != null && parentToLink != null)
    {
     // Get the static relationship and role (= end of relationship):
     DomainRelationshipInfo relationshipFrom = parentFromLink.GetDomainRelationship();
     DomainRoleInfo parentFromRole = relationshipFrom.DomainRoles[0];
     // Get the node in which the element is embedded, usually the element displayed in the shape:
     ModelElement parentFrom = parentFromLink.LinkedElements[0];

     // Same again for the target:
     DomainRelationshipInfo relationshipTo = parentToLink.GetDomainRelationship();
     DomainRoleInfo parentToRole = relationshipTo.DomainRoles[0];
     ModelElement parentTo = parentToLink.LinkedElements[0];

     // Mouse went down and up in same parent and same compartment:
     if (parentTo == parentFrom && relationshipTo == relationshipFrom)
     {
      // Find index of target position:
      int newIndex = 0;
      var elementLinks = parentToRole.GetElementLinks(parentTo);
      foreach (ElementLink link in elementLinks)
      {
       if (link == parentToLink) { break; }
       newIndex++;
      }

      if (newIndex < elementLinks.Count)
      {
       using (Transaction t = parentFrom.Store.TransactionManager.BeginTransaction("Move list item"))
       {
        parentFromLink.MoveToIndex(parentFromRole, newIndex);
        t.Commit();
       }
      }
     }
    }
   }
  }

  /// <summary>
  /// Get the embedding link to this element.
  /// Assumes there is no inheritance between embedding relationships.
  /// (If there is, you need to make sure you've got the relationship
  /// that is represented in the shape compartment.)
  /// </summary>
  /// <param name="child"></param>
  /// <returns></returns>
  ElementLink GetEmbeddingLink(ClassModelElement child)
  {
   foreach (DomainRoleInfo role in child.GetDomainClass().AllEmbeddedByDomainRoles)
   {
    foreach (ElementLink link in role.OppositeDomainRole.GetElementLinks(child))
    {
     // Just the assume the first embedding link is the only one.
     // Not a valid assumption if one relationship is derived from another.
     return link;
    }
   }
   return null;
  }
 }
}
```

## <a name="see-also"></a>추가 정보

- [복사 동작 사용자 지정](../modeling/customizing-copy-behavior.md)
- [도메인별 언어 솔루션 배포](msi-and-vsix-deployment-of-a-dsl.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

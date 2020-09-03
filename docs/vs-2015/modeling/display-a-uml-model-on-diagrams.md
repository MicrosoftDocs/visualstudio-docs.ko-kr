---
title: 다이어그램에 UML 모델 표시 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: adf1f1f2-2ad9-4ade-82de-c6a5194ab471
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06a22161068dd7604fe7bb4153e322c0954b89d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533020"
---
# <a name="display-a-uml-model-on-diagrams"></a>다이어그램에 UML 모델 표시
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 확장에 대한 프로그램 코드에서 모델 요소가 다이어그램에 표시되는 방식을 제어할 수 있습니다. UML 모델을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

이 항목의 내용:
- [다이어그램에 요소를 표시하려면](#Display)

- [요소를 나타내는 모양 액세스](#GetShapes)

- [모양 이동 및 크기 조정](#Moving)

- [다이어그램에서 모양을 제거하려면](#Removing)

- [다이어그램 열기 및 만들기](#Opening)

- [예: 모양 맞춤 명령](#AlignCommand)

## <a name="to-display-an-element-on-a-diagram"></a><a name="Display"></a> 다이어그램에 요소를 표시 하려면
 사용 사례 또는 작업과 같은 요소를 만들면 사용자가 UML 모델 탐색기에서 볼 수 있지만 다이어그램에 항상 자동으로 표시되지는 않습니다. 표시하는 코드를 작성해야 하는 경우도 있습니다. 다음 표에서는 대체 방법을 요약해서 보여 줍니다.

|요소의 형식|예를 들면 다음과 같습니다.|표시를 위해 코드에서 수행해야 하는 작업|
|---------------------|-----------------|-------------------------------------|
|분류자|`Class`<br /><br /> `Component`<br /><br /> `Actor`<br /><br /> `Use Case`|지정한 다이어그램에서 연결된 모양을 만듭니다. 각 분류자에 대한 모양을 원하는 개수만큼 만들 수 있습니다.<br /><br /> `diagram.Display<modelElementType>`<br /><br /> `(modelElement, parentShape,`<br /><br /> `xPosition , yPosition);`<br /><br /> 다이어그램의 최상위 모양에 대해 `parentShape`를 `null`로 설정합니다.<br /><br /> 다른 모양 안에 모양을 표시하려면<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `useCaseDiagram.Display`<br /><br /> `(useCase,`<br /><br /> `subsystemShape,`<br /><br /> `subsystemShape.XPosition + 5,`<br /><br /> `subsystemShape.YPosition + 5);`**참고:**  **ILinkedUndo** 트랜잭션 내부에서 표시를 수행 하는 경우 메서드는 때때로 no를 반환 `IShape` 합니다. 그러나 모양은 올바르게 생성되며 `IElement.Shapes().`를 사용하여 액세스할 수 있습니다.|
|분류자의 자식|특성, 작업,<br /><br /> 파트, 포트|자동 - 코드가 필요하지 않습니다.<br /><br /> 부모의 일부로 표시됩니다.|
|동작|상호 작용(시퀀스),<br /><br /> 활동|해당 다이어그램에 동작을 바인딩합니다.<br /><br /> 한 번에 최대 하나의 다이어그램에 각 동작을 바인딩할 수 있습니다.<br /><br /> 예를 들면 다음과 같습니다.<br /><br /> `sequenceDiagram.Bind(interaction);`<br /><br /> `activityDiagram.Bind(activity);`|
|동작의 자식|수명선, 메시지, 작업, 개체 노드|자동 - 코드가 필요하지 않습니다.<br /><br /> 부모가 다이어그램에 바인딩된 경우 표시됩니다.|
|관계|연결, 일반화, 흐름, 종속성|자동 - 코드가 필요하지 않습니다.<br /><br /> 양쪽 끝이 표시되는 모든 다이어그램에 표시됩니다.|

## <a name="accessing-the-shapes-that-represent-an-element"></a><a name="GetShapes"></a> 요소를 나타내는 도형에 액세스
 요소를 나타내는 모양은 다음 형식에 속합니다.

 `IShape`

 `IShape<` *ElementType* `>`

 여기서 *ElementType* 은 또는와 같은 모델 요소의 형식입니다 `IClass` `IUseCase` .

|구문|Description|
|-|-|
|`anElement.Shapes ()`|열려 있는 다이어그램에서 이 요소를 나타내는 모든 `IShapes`입니다.|
|`anElement.Shapes(aDiagram)`|특정 다이어그램에서 이 요소를 나타내는 모든 `IShapes`입니다.|
|`anIShape.GetElement()`|모양이 나타내는 `IElement`입니다. 일반적으로 IElement의 서브클래스로 캐스팅합니다.|
|`anIShape.Diagram`|모양을 포함하는 `IDiagram`입니다.|
|`anIShape.ParentShape`|`anIShape`를 포함하는 모양입니다. 예를 들어 포트 모양은 구성 요소 모양 안에 포함됩니다.|
|`anIShape.ChildShapes`|`IShape` 또는 `IDiagram` 안에 포함된 모양입니다.|
|`anIShape.GetChildShapes<IUseCase>()`|`IShape` 또는 `IDiagram` 안에 포함되고, `IUseCase`와 같은 지정된 형식의 요소를 나타내는 모양입니다.|
|`IShape iShape = ...;`<br /><br /> `IShape<IClass> classShape = iShape.ToIShape<IClass>();`<br /><br /> `IClass aClass = classShape.Element;`|제네릭 `IShape`를 강력한 형식의 `IShape<IElement>`로 캐스팅합니다.|
|`IShape<IClassifier> classifierShape;`<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `classifierShape.ToIShape<IUseCase>();`|매개 변수가 있는 모양 형식 간에 모양을 캐스팅합니다.|

## <a name="moving-and-resizing-shapes"></a><a name="Moving"></a> 셰이프 이동 및 크기 조정

|구문|Description|
|-|-|
|`anIShape.Move(x, y, [width], [height])`|모양을 이동하거나 크기를 조정합니다.|
|`IDiagram.EnsureVisible( IEnumerable<IShape> shapes, bool zoomToFit = false)`|창을 활성화하고 지정된 모양이 모두 표시되도록 다이어그램을 스크롤합니다. 모양이 모두 다이어그램에 있어야 합니다. `zoomToFit`이 true이면 필요한 경우 모든 모양이 표시되도록 다이어그램의 크기가 조정됩니다.|

 예제는 [맞춤 명령 정의](#AlignCommand)를 참조 하세요.

## <a name="to-remove-a-shape-from-a-diagram"></a><a name="Removing"></a> 다이어그램에서 모양을 제거 하려면
 요소를 삭제하지 않고 일부 형식의 요소 모양을 삭제할 수 있습니다.

|모델 요소|모양을 제거하려면|
|-------------------|-------------------------|
|분류자: 클래스, 인터페이스, 열거형, 행위자, 사용 사례 또는 구성 요소|`shape.Delete();`|
|동작: 상호 작용 또는 동작|프로젝트에서 다이어그램을 삭제할 수 있습니다. `IDiagram.FileName`을 사용하여 경로를 가져옵니다.<br /><br /> 이 경우 모델에서 동작이 삭제되지 않습니다.|
|다른 모든 모양|다른 모양은 다이어그램에서 명시적으로 삭제할 수 없습니다. 모델에서 요소를 삭제하거나 다이어그램에서 부모 모양을 제거하면 모양이 자동으로 사라집니다.|

## <a name="opening-and-creating-diagrams"></a><a name="Opening"></a> 다이어그램 열기 및 만들기

### <a name="to-access-the-users-current-diagram-from-a-command-or-gesture-extension"></a>명령 또는 제스처 확장에서 사용자의 현재 다이어그램에 액세스하려면
 클래스에서 가져온 이 속성을 선언합니다.

 `[Import]`

 `IDiagramContext Context { get; set; }`

 메서드에서 다이어그램에 액세스합니다.

 `IClassDiagram classDiagram =`

 `Context.CurrentDiagram as IClassDiagram;`

> [!NOTE]
> `IDiagram` 인스턴스(및 `IClassDiagram`과 같은 하위 형식)는 처리 중인 명령 내에서만 유효합니다. 제어가 사용자에게 반환하는 동안 지속되는 변수에 `IDiagram` 개체를 유지하지 않는 것이 좋습니다.

 자세한 내용은 [모델링 다이어그램에서 메뉴 명령 정의](../modeling/define-a-menu-command-on-a-modeling-diagram.md)를 참조 하세요.

### <a name="to-obtain-a-list-of-open-diagrams"></a>열려 있는 다이어그램 목록을 가져오려면
 프로젝트에서 현재 열려 있는 다이어그램의 목록입니다.

```
Context.CurrentDiagram.ModelStore.Diagrams()
```

## <a name="to-access-the-diagrams-in-a-project"></a>프로젝트에서 다이어그램에 액세스하려면
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] API를 사용하여 모델링 프로젝트 및 다이어그램을 열고 만들 수 있습니다.

 `EnvDTE.ProjectItem`에서 `IDiagramContext`로의 캐스트를 확인합니다.

```

      using EnvDTE; // Visual Studio API
...
[Import]
public IServiceProvider ServiceProvider { get; set; }
...
// Get Visual Studio API
DTE dte = ServiceProvider.GetService(typeof(DTE)) as DTE;
// Get current Visual Studio project
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;
// Open and process every diagram in the project.
foreach (ProjectItem item in project.ProjectItems)
{
  // Cast ProjectItem to IDiagramContext
  IDiagramContext context = item as IDiagramContext;
  if (context == null)
  {
     // This is not a diagram file.
     continue;
  }
  // Open the file and give the window the focus.
  if (!item.IsOpen)
  {
      item.Open().Activate();
  }
  // Get the diagram.
  IDiagram diagram = context.CurrentDiagram;
  // Deal with specific diagram types.
  ISequenceDiagram seqDiagram = diagram as ISequenceDiagram;
  if (seqDiagram != null)
  { ... } } }
```

 제어가 `IDiagram`로 반환된 후에는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 인스턴스 및 해당 하위 형식이 유효하지 않습니다.

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트에서 모델 저장소를 가져올 수도 있습니다.

```

      Project project = ...;
IModelStore modelStore = (project as IModelingProject).Store;
```

## <a name="example-command-for-aligning-shapes"></a><a name="AlignCommand"></a> 예: 셰이프를 정렬 하는 명령
 다음 코드에서를 깔끔하게 모양을 맞추는 메뉴 명령을 구현합니다. 먼저 사용자가 두 개 이상의 모양을 세로 또는 가로로 대충 맞춰서 배치해야 합니다. 그런 후에 맞춤 명령을 사용하여 가운데 맞춤을 수행할 수 있습니다.

 명령을 사용할 수 있게 하려면 메뉴 명령 프로젝트에 다음 코드를 추가하고 결과로 생성된 확장을 사용자에게 배포합니다. 자세한 내용은 [모델링 다이어그램에서 메뉴 명령 정의](../modeling/define-a-menu-command-on-a-modeling-diagram.md)를 참조 하세요.

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace AlignCommand
{
  // Implements a command to align shapes in a UML class diagram.
  // The user first selects shapes that are roughly aligned either vertically or horizontally.
  // This command will straighten them up.

  // Place this file in a menu command extension project.
  // See https://msdn.microsoft.com/library/ee329481.aspx

  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension] // TODO: Add other diagram types if needed
  class CommandExtension : ICommandExtension
  {
    /// <summary>
    /// See https://msdn.microsoft.com/library/ee329481.aspx
    /// </summary>
    [Import]
    IDiagramContext context { get; set; }

    /// <summary>
    /// Transaction context.
    /// See https://msdn.microsoft.com/library/ee330926.aspx
    /// </summary>
    [Import]
    ILinkedUndoContext linkedUndo { get; set; }

    /// <summary>
    /// Called when the user selects the command.
    /// </summary>
    /// <param name="command"></param>
    public void Execute(IMenuCommand command)
    {
      Align(context.CurrentDiagram.SelectedShapes);
    }

    /// <summary>
    /// Called when the user right-clicks on the diagram.
    /// Determines whether the command is enabled.
    /// </summary>
    /// <param name="command"></param>
    public void QueryStatus(IMenuCommand command)
    {
      IEnumerable<IShape> currentSelection = context.CurrentDiagram.SelectedShapes;
      // Make it visible if there are shapes selected:
      command.Visible = currentSelection.Count() > 0 && !(currentSelection.FirstOrDefault() is IDiagram);

      // Make it enabled if there are two or more shapes that are roughly in line:
      command.Enabled = currentSelection.Count() > 1
        && (HorizontalAlignCenter(currentSelection) > 0.0
        || VerticalAlignCenter(currentSelection) > 0.0);

    }

    /// <summary>
    /// Title of the menu command.
    /// </summary>
    public string Text
    {
      get { return "Align Shapes"; }
    }

    /// <summary>
    /// Find a horizontal line that goes through a list of shapes.
    /// </summary>
    /// <param name="shapes"></param>
    /// <returns></returns>
    private static double HorizontalAlignCenter(IEnumerable<IShape> shapes)
    {
      double Y = -1.0;
      double top = 0.0, bottom = shapes.First().Bottom();
      foreach (IShape shape in shapes)
      {
        top = Math.Max(top, shape.Top());
        bottom = Math.Min(bottom, shape.Bottom());
      }
      if (bottom > top) Y = (bottom + top) / 2.0;
      return Y;
    }

    /// <summary>
    /// Find a vertical line that goes through a list of shapes.
    /// </summary>
    /// <param name="shapes"></param>
    /// <returns></returns>
    private static double VerticalAlignCenter(IEnumerable<IShape> shapes)
    {
      double X = -1.0;
      double left = 0.0, right = shapes.First().Right();
      foreach (IShape shape in shapes)
      {
        left = Math.Max(left, shape.Left());
        right = Math.Min(right, shape.Right());
      }
      if (right > left) X = (right + left) / 2.0;
      return X;
    }

    /// <summary>
    /// Line up those shapes that are roughly aligned.
    /// </summary>
    /// <param name="shapes"></param>
    private void Align(IEnumerable<IShape> shapes)
    {
      if (shapes.Count() > 1)
      {
        // The shapes must all overlap either horizontally or vertically.
        // Find a horizontal line that is covered by all the shapes:
        double Y = HorizontalAlignCenter(shapes);
        if (Y > 0.0) // Negative if they don't overlap.
        {
          // Adjust all the shape positions in one transaction:
          using (ILinkedUndoTransaction t = linkedUndo.BeginTransaction("align"))
          {
            foreach (IShape shape in shapes)
            {
              shape.AlignYCenter(Y);
            }
            t.Commit();
          }
        }
        else
        {
          // Find a vertical line that is covered by all the shapes:
          double X = VerticalAlignCenter(shapes);
          if (X > 0.0) // Negative if they don't overlap.
          {
            // Adjust all the shape positions in one transaction:
            using (ILinkedUndoTransaction t = linkedUndo.BeginTransaction("align"))
            {
              foreach (IShape shape in shapes)
              {
                shape.AlignXCenter(X);
              }
              t.Commit();
            }
          }
        }
      }
    }
  }

  /// <summary>
  /// Convenience extensions for IShape.
  /// </summary>
  public static class IShapeExtension
  {
    public static double Bottom(this IShape shape)
    {
      return shape.YPosition + shape.Height;
    }

    public static double Top(this IShape shape)
    {
      return shape.YPosition;
    }

    public static double Left(this IShape shape)
    {
      return shape.XPosition;
    }

    public static double Right(this IShape shape)
    {
      return shape.XPosition + shape.Width;
    }

    public static void AlignYCenter(this IShape shape, double Y)
    {
      shape.Move(shape.XPosition, Y - shape.YCenter());
    }

    public static void AlignXCenter(this IShape shape, double X)
    {
      shape.Move(X - shape.XCenter(), shape.YPosition);
    }

    /// <summary>
    /// We can adjust what bit of the shape we want to be aligned.
    /// The default is the center of the shape.
    /// </summary>
    /// <param name="shape"></param>
    /// <returns></returns>
    public static double YCenter(this IShape shape)
    {
        return shape.Height / 2.0;
    }

    /// <summary>
    /// We can adjust what bit of the shape we want to be aligned.
    /// The default is the center of the shape.
    /// </summary>
    /// <param name="shape"></param>
    /// <returns></returns>
    public static double XCenter(this IShape shape)
    {
        return shape.Width / 2.0;
    }
  }
}

```

## <a name="see-also"></a>관련 항목
 [Uml 모델 및 다이어그램 확장](../modeling/extend-uml-models-and-diagrams.md) [uml 모델 탐색](../modeling/navigate-the-uml-model.md)
 
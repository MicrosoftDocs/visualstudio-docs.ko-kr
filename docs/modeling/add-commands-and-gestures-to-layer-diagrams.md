---
title: 종속성 다이어그램에 명령 및 제스처 추가
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency diagrams, adding custom commands
- dependency diagrams, adding custom gestures
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ff23e07bd6e81b11d94a8256c33b57b4b0c558c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85531393"
---
# <a name="add-commands-and-gestures-to-dependency-diagrams"></a>종속성 다이어그램에 명령 및 제스처 추가

Visual Studio에서 종속성 다이어그램에 대 한 마우스 오른쪽 단추 클릭 메뉴 명령 및 제스처 처리기를 정의할 수 있습니다. 이러한 확장을 다른 Visual Studio 사용자에게 배포할 수 있는 VSIX(Visual Studio Integration Extension)로 패키지할 수 있습니다.

필요한 경우 동일한 Visual Studio 프로젝트에서 여러 개의 명령 및 제스처 처리기를 정의할 수 있습니다. 이러한 여러 프로젝트를 하나의 VSIX에 결합할 수도 있습니다. 예를 들어 계층 명령과 도메인별 언어를 포함 하는 단일 VSIX를 정의할 수 있습니다.

> [!NOTE]
> 사용자의 소스 코드를 종속성 다이어그램과 비교 하는 아키텍처 유효성 검사를 사용자 지정할 수도 있습니다. 별도의 Visual Studio 프로젝트에서 아키텍처 유효성 검사를 정의해야 합니다. 동일한 VSIX에 다른 확장으로 추가할 수 있습니다. 자세한 내용은 [종속성 다이어그램에 사용자 지정 아키텍처 유효성 검사 추가](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

[요구 사항](../modeling/extend-layer-diagrams.md#requirements)을 참조 하세요.

## <a name="define-a-command-or-gesture-in-a-new-vsix"></a>새 VSIX에서 명령 또는 제스처 정의

확장을 만드는 가장 빠른 방법은 프로젝트 템플릿을 사용하는 것입니다. 이 방법에서는 코드 및 VSIX 매니페스트를 동일한 프로젝트에 배치합니다.

1. 새 **레이어 디자이너 명령 확장** 또는 **레이어 디자이너 제스처 확장** 프로젝트를 만듭니다.

   템플릿에서 작은 작업 예제가 포함된 프로젝트를 만듭니다.

2. 확장을 테스트 하려면 **ctrl** + **f5** 또는 **f5**키를 누릅니다.

    Visual Studio의 실험적 인스턴스가 시작 됩니다. 이 인스턴스에서 종속성 다이어그램을 만듭니다. 이 다이어그램에서 명령 또는 제스처 확장이 작동해야 합니다.

3. 실험적 인스턴스를 닫고 샘플 코드를 수정합니다.

4. 동일한 프로젝트에 명령 또는 제스처 처리기를 더 추가할 수 있습니다. 자세한 내용은 다음 섹션 중 하나를 참조하세요.

    [메뉴 명령 정의](#command)

    [제스처 처리기 정의](#gesture)

::: moniker range="vs-2017"

5. Visual Studio의 주 인스턴스 또는 다른 컴퓨터에 확장을 설치 하려면 *bin* 디렉터리에서 *.vsix* 파일을 찾습니다. 설치할 컴퓨터로 파일을 복사하고 파일을 두 번 클릭합니다. 제거 하려면 **도구** 메뉴에서 **확장 및 업데이트** 를 선택 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

5. Visual Studio의 주 인스턴스 또는 다른 컴퓨터에 확장을 설치 하려면 *bin* 디렉터리에서 *.vsix* 파일을 찾습니다. 설치할 컴퓨터로 파일을 복사하고 파일을 두 번 클릭합니다. 제거 하려면 **확장** 메뉴에서 **확장 관리** 를 선택 합니다.

::: moniker-end

## <a name="add-a-command-or-gesture-to-a-separate-vsix"></a>별도 VSIX에 명령 또는 제스처 추가

명령, 레이어 유효성 검사기 및 기타 확장이 포함된 하나의 VSIX를 만들려면 VSIX를 정의하는 프로젝트 하나와 처리기에 대한 개별 프로젝트를 만드는 것이 좋습니다.

1. 새 **클래스 라이브러리** 프로젝트를 만듭니다. 이 프로젝트는 명령 또는 제스처 처리기 클래스를 포함합니다.

   > [!NOTE]
   > 한 클래스 라이브러리에서 두 개 이상의 명령 또는 제스처 처리기 클래스를 정의할 수 있지만, 별도 클래스 라이브러리에서 레이어 유효성 검사 클래스를 정의해야 합니다.

2. 솔루션에서 VSIX 프로젝트를 추가 하거나 만듭니다. VSIX 프로젝트에는 이름이 **source.extension.vsixmanifest**인 파일이 포함 되어 있습니다.

3. **솔루션 탐색기**에서 VSIX 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **시작 프로젝트로 설정**을 선택 합니다.

4. **source.extension.vsixmanifest**의 **자산**에서 명령 또는 제스처 처리기 프로젝트를 MEF 구성 요소로 추가합니다.

    1. **자산**탭에서 **새로 만들기**를 선택합니다.

    2. **형식**에서 **Microsoft.VisualStudio.MefComponent**를 선택합니다.

    3. **소스**에서 **현재 솔루션의 프로젝트** 를 선택한 다음 명령 또는 제스처 처리기 프로젝트의 이름을 선택합니다.

    4. 파일을 저장합니다.

5. 명령 또는 제스처 처리기 프로젝트로 돌아가서 다음 프로젝트 참조를 추가 합니다.

   |**참조**|**수행할 수 있는 기능**|
   |-|-|
   |Program Files\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|레이어 만들기 및 편집|
   |Microsoft.VisualStudio.Uml.Interfaces|레이어 만들기 및 편집|
   |Microsoft.VisualStudio.ArchitectureTools.Extensibility|다이어그램에서 모양 수정|
   |System.ComponentModel.Composition|MEF(Managed Extensibility Framework)를 사용하여 구성 요소 정의|
   |Microsoft.VisualStudio.Modeling.Sdk.[version]|모델링 확장 정의|
   |Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]|모양 및 다이어그램 업데이트|

6. 확장에 대한 코드가 포함되도록 C# 클래스 라이브러리 프로젝트의 클래스 파일을 편집합니다. 자세한 내용은 다음 섹션 중 하나를 참조하세요.

     [메뉴 명령 정의](#command)

     [제스처 처리기 정의](#gesture)

7. 기능을 테스트 하려면 **ctrl** + **f5** 또는 **f5**키를 누릅니다.

   Visual Studio의 실험적 인스턴스가 열립니다. 이 인스턴스에서 종속성 다이어그램을 만들거나 엽니다.

8. Visual Studio의 주 인스턴스 또는 다른 컴퓨터에 VSIX를 설치 하려면 VSIX 프로젝트의 **bin** 디렉터리에서 **.vsix** 파일을 찾습니다. VSIX를 설치할 컴퓨터에 파일을 복사합니다. 파일 탐색기에서 VSIX 파일을 두 번 클릭 합니다.

## <a name="defining-a-menu-command"></a><a name="command"></a> 메뉴 명령 정의

기존 제스처 또는 명령 프로젝트에 메뉴 명령 정의를 더 추가할 수 있습니다. 각 명령은 다음과 같은 특징이 있는 클래스에 의해 정의됩니다.

- 클래스는 다음과 같이 선언됩니다.

   `[LayerDesignerExtension]`

   `[Export(typeof(ICommandExtension))]`

   `public class`  *MyLayerCommand*  `: ICommandExtension { ... }`

- 네임스페이스 및 클래스 이름은 중요하지 않습니다.

- `ICommandExtension` 을 구현하는 메서드는 다음과 같습니다.

  - `string Text {get;}` - 메뉴에 표시되는 레이블입니다.

  - `void QueryStatus(IMenuCommand command)` - 사용자가 다이어그램을 마우스 오른쪽 단추로 클릭할 때 호출되며 사용자의 현재 선택 항목에 대해 명령이 표시되고 사용할 수 있어야 하는지 여부를 확인합니다.

  - `void Execute(IMenuCommand command)` - 사용자가 명령을 선택할 때 호출됩니다.

- 현재 선택 항목을 확인하기 위해 `IDiagramContext`를 가져올 수 있습니다.

   `[Import]`

   `public IDiagramContext DiagramContext { get; set; }`

   `...`

   `DiagramContext.CurrentDiagram.SelectedShapes.Count()...`

새 명령을 추가하려면 다음 샘플을 포함하는 새 코드 파일을 만듭니다. 그런 다음 파일을 테스트하고 편집합니다.

```csharp
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;

namespace MyLayerExtension // Change to your preference.
{
  // This is a feature for dependency diagrams:
  [LayerDesignerExtension]
  // This feature is a menu command:
  [Export(typeof(ICommandExtension))]
  // Change the class name to your preference:
  public class MyLayerCommand : ICommandExtension
  {
    [Import]
    public IDiagramContext DiagramContext { get; set; }

    [Import]
    public ILinkedUndoContext LinkedUndoContext { get; set; }

    // Menu command label:
    public string Text
    {
      get { return "Duplicate layers"; }
    }

    // Called when the user right-clicks the diagram.
    // Defines whether the command is visible and enabled.
    public void QueryStatus(IMenuCommand command)
    {
      command.Visible =
      command.Enabled = DiagramContext.CurrentDiagram
        .SelectedShapes.Count() > 0;
    }

    // Called when the user selects the command.
    public void Execute(IMenuCommand command)
    {
      // A selection of starting points:
      IDiagram diagram = this.DiagramContext.CurrentDiagram;
      ILayerModel lmodel = diagram.GetLayerModel();
      foreach (ILayer layer in lmodel.Layers)
      { // All layers in model.
      }
      // Updates should be performed in a transaction:
      using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("copy selection"))
      {
        foreach (ILayer layer in
          diagram.SelectedShapes
            .Select(shape=>shape.GetLayerElement())
            .Where(element => element is ILayer))
        {
          ILayer copy = lmodel.CreateLayer(layer.Name + "+");
          // Position the shapes:
          IShape originalShape = layer.GetShape();
          copy.GetShape().Move(
            originalShape.XPosition + originalShape.Width * 1.2,
            originalShape.YPosition);
        }
        t.Commit();
      }
    }
  }
}
```

## <a name="defining-a-gesture-handler"></a><a name="gesture"></a> 제스처 처리기 정의

제스처 처리기는 사용자가 항목을 종속성 다이어그램으로 끌 때 그리고 사용자가 다이어그램에서 아무 곳 이나 두 번 클릭할 때 응답 합니다.

기존 명령 또는 제스처 처리기 VSIX 프로젝트에 제스처 처리기를 정의하는 코드 파일을 추가할 수 있습니다.

```csharp
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;

namespace MyLayerExtensions // change to your preference
{
  [LayerDesignerExtension]
  [Export(typeof(IGestureExtension))]
  public class MyLayerGestureHandler : IGestureExtension
  {
  }
}
```

제스처 처리기와 관련하여 다음 사항에 주의하세요.

- `IGestureExtension` 의 멤버는 다음과 같습니다.

     **OnDoubleClick** - 사용자가 다이어그램을 두 번 클릭할 때 호출됩니다.

     **CanDragDrop** - 사용자가 항목을 다이어그램으로 끄는 동안 마우스를 이동할 때 반복적으로 호출됩니다. 신속하게 작동해야 합니다.

     **OnDragDrop** - 사용자가 다이어그램에 항목을 놓을 때 호출됩니다.

- 각 메서드의 첫 번째 인수는 `IShape`로, 여기서 레이어 요소를 가져올 수 있습니다. 예:

    ```csharp
    public void OnDragDrop(IShape target, IDataObject data)
    {
        ILayerElement element = target.GetLayerElement();
        if (element is ILayer)
        {
            // ...
        }
    }
    ```

- 일부 형식의 끌어온 항목에 대한 처리기는 이미 정의되었습니다. 예를 들어 사용자가 솔루션 탐색기에서 종속성 다이어그램으로 항목을 끌어올 수 있습니다. 이러한 형식의 항목에 대한 끌기 처리기는 정의할 수 없습니다. 이 경우 `DragDrop` 메서드가 호출되지 않습니다.

## <a name="see-also"></a>참조

- [종속성 다이어그램에 사용자 지정 아키텍처 유효성 검사 추가](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

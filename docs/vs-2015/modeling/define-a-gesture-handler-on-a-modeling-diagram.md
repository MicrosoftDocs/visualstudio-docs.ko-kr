---
title: 모델링 다이어그램에서 제스처 처리기 정의 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, double-click
- UML - extending, drag and drop
ms.assetid: e5e1d70a-3539-4321-a3b1-89e86e4d6430
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: af4123b24ab9286e306a1034de4416a31ae76f2b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533070"
---
# <a name="define-a-gesture-handler-on-a-modeling-diagram"></a>모델링 다이어그램의 제스처 처리기 정의
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 사용자가 항목을 두 번 클릭하거나 UML 다이어그램으로 끌 때 수행되는 명령을 정의할 수 있습니다. 이러한 확장을[VSIX](https://msdn.microsoft.com/library/dd393694(VS.100).aspx)(Visual Studio Integration Extension)로 패키징하고 다른 Visual Studio 사용자에게 배포할 수 있습니다.

 끌려는 요소 형식 및 다이어그램 형식에 대한 기본 제공 동작이 이미 있으면 이 동작에 추가하거나 이 동작을 재정의하지 못할 수 있습니다.

## <a name="requirements"></a>요구 사항
 [요구 사항](../modeling/extend-uml-models-and-diagrams.md#Requirements)을 참조 하세요.

 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

## <a name="creating-a-gesture-handler"></a>제스처 처리기 만들기
 UML 디자이너에 대한 제스처 처리기를 정의하려면 제스처 처리기의 동작을 정의하는 클래스를 만들고 해당 클래스를 VSIX(Visual Studio Integration Extension)에 포함해야 합니다. VSIX는 처리기를 설치할 수 있는 컨테이너로 사용됩니다. 제스처 처리기를 정의하는 두 가지 대체 방법은 다음과 같습니다.

- **프로젝트 템플릿을 사용하여 자체 VSIX에서 제스처 처리기를 만듭니다.** 이는 더 빠른 방법입니다. 처리기를 유효성 검사 확장, 사용자 지정 도구 상자 또는 메뉴 명령과 같은 다른 형식 확장과 결합하지 않으려면 이 방법을 사용합니다.

- **개별 제스처 처리기 및 VSIX 프로젝트를 만듭니다.** 여러 확장 형식을 같은 VSIX로 결합하려면 이 방법을 사용합니다. 예를 들어 제스처 처리기에서 모델이 특정 제약 조건을 따르도록 요구하면 유효성 검사 방법과 동일한 VSIX에 해당 제스처 처리기를 포함할 수 있습니다.

#### <a name="to-create-a-gesture-handler-in-its-own-vsix"></a>자체 VSIX에서 제스처 처리기를 만들려면

1. **새 프로젝트** 대화 상자의 **모델링 프로젝트**에서 **제스처 확장**을 선택합니다.

2. 새 프로젝트에서 **.cs** 파일을 열고 `GestureExtension` 클래스를 수정하여 제스처 처리기를 구현합니다.

    자세한 내용은 [제스처 처리기 구현](#Implementing)을 참조하세요.

3. F5 키를 눌러 제스처 처리기를 테스트합니다. 자세한 내용은 [제스처 처리기 실행](#Executing)을 참조하세요.

4. 프로젝트에서 작성 한 파일 **bin \\ \* \\ \* . vsix** 를 복사 하 여 다른 컴퓨터에 제스처 처리기를 설치 합니다. 자세한 내용은 [확장 설치 및 제거](#Installing)를 참조하세요.

   다음은 대체 절차입니다.

#### <a name="to-create-a-separate-class-library-dll-project-for-the-gesture-handler"></a>제스처 처리기에 대한 별도 클래스 라이브러리(DLL) 프로젝트를 만들려면

1. 새 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션이나 기존 솔루션에서 클래스 라이브러리 프로젝트를 만듭니다.

   1. **파일** 메뉴에서 **새로 만들기**, **프로젝트**를 차례로 선택합니다.

   2. **설치된 템플릿**에서 **Visual C#** 또는 **Visual Basic**을 확장하고 가운데 열에서 **클래스 라이브러리**를 선택합니다.

2. 프로젝트에 다음 참조를 추가합니다.

    `Microsoft.VisualStudio.Modeling.Sdk.[version]`

    `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]`

    `Microsoft.VisualStudio.ArchitectureTools.Extensibility`

    `Microsoft.VisualStudio.Uml.Interfaces`

    `System.ComponentModel.Composition`

    `System.Windows.Forms`

    `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer` – 레이어 다이어그램을 확장할 경우에만 필요합니다. 자세한 내용은 [레이어 다이어그램 확장](../modeling/extend-layer-diagrams.md)을 참조 하세요.

3. 프로젝트에 클래스 파일을 추가하고 해당 콘텐츠를 다음 코드로 설정합니다.

   > [!NOTE]
   > 원하는 대로 네임스페이스 및 클래스 이름을 변경합니다.

   ```
   using System.ComponentModel.Composition;
   using System.Linq;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Modeling.Diagrams;
   using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
   using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
   using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;
   using Microsoft.VisualStudio.Modeling;
   using Microsoft.VisualStudio.Uml.Classes;
   // ADD other UML namespaces if required

   namespace MyGestureHandler // CHANGE
   {
     // DELETE any of these attributes if the handler
     // should not work with some types of diagram.
     [ClassDesignerExtension]
     [ActivityDesignerExtension]
     [ComponentDesignerExtension]
     [SequenceDesignerExtension]
     [UseCaseDesignerExtension]
     // [LayerDesignerExtension]

     // Gesture handlers must export IGestureExtension:
     [Export(typeof(IGestureExtension))]
     // CHANGE class name
     public class MyGesture1 : IGestureExtension
     {
       [Import]
       public IDiagramContext DiagramContext { get; set; }

       /// <summary>
       /// Called when the user double-clicks on the diagram
       /// </summary>
       /// <param name="targetElement"></param>
       /// <param name="diagramPointEventArgs"></param>
       public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.

         // Get the target shape, if any. Null if the target is the diagram.
         IShape targetIShape = targetElement.CreateIShape();

         // Do something...
       }

       /// <summary>
       /// Called repeatedly when the user drags from anywhere on the screen.
       /// Return value should indicate whether a drop here is allowed.
       /// </summary>
       /// <param name="targetMergeElement">References the element to be dropped on.</param>
       /// <param name="diagramDragEventArgs">References the element to be dropped.</param>
       /// <returns></returns>
       public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.

         // Get the target element, if any. Null if the target is the diagram.
         IShape targetIShape = targetMergeElement.CreateIShape();

         // This example allows drag of any UML elements.
         return GetModelElementsFromDragEvent(diagramDragEventArgs).Count() > 0;
       }

       /// <summary>
       /// Execute the action to be performed on the drop.
       /// </summary>
       /// <param name="targetDropElement"></param>
       /// <param name="diagramDragEventArgs"></param>
       public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.
       }

       /// <summary>
       /// Retrieves UML IElements from drag arguments.
       /// Works for drags from UML diagrams.
       /// </summary>
       private IEnumerable<IElement> GetModelElementsFromDragEvent
               (DiagramDragEventArgs dragEvent)
       {
         //ElementGroupPrototype is the container for
         //dragged and copied elements and toolbox items.
         ElementGroupPrototype prototype =
            dragEvent.Data.
            GetData(typeof(ElementGroupPrototype))
                 as ElementGroupPrototype;
         // Locate the originals in the implementation store.
         IElementDirectory implementationDirectory =
            dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;

         return prototype.ProtoElements.Select(
           prototypeElement =>
           {
             ModelElement element = implementationDirectory
               .FindElement(prototypeElement.ElementId);
             ShapeElement shapeElement = element as ShapeElement;
             if (shapeElement != null)
             {
               // Dragged from a diagram.
               return shapeElement.ModelElement as IElement;
             }
             else
             {
               // Dragged from UML Model Explorer.
               return element as IElement;
             }
           });
       }

     }
   }

   ```

    메서드에 삽입할 항목에 대한 자세한 내용은 [제스처 처리기 구현](#Implementing)을 참조하세요.

   명령을 설치할 컨테이너로 사용되는 VSIX 프로젝트에 메뉴 명령을 추가해야 합니다. 필요하면 같은 VSIX에 다른 구성 요소를 포함할 수 있습니다.

#### <a name="to-add-a-separate-gesture-handler-to-a-vsix-project"></a>VSIX 프로젝트에 개별 제스처 처리기를 추가하려면

1. 자체 VSIX를 사용하여 제스처 처리기를 만든 경우에는 이 절차가 필요하지 않습니다.

2. 솔루션에 VSIX 프로젝트가 없으면 VSIX 프로젝트를 만듭니다.

    1. **솔루션 탐색기**의 솔루션 바로 가기 메뉴에서 **추가**, **새 프로젝트**를 차례로 선택 합니다.

    2. **설치된 템플릿**에서 **Visual C#** 또는 **Visual Basic**을 확장한 다음 **확장성**을 선택합니다. 가운데 열에서 **VSIX 프로젝트**를 선택합니다.

3. VSIX 프로젝트를 솔루션의 시작 프로젝트로 설정합니다.

    - 솔루션 탐색기의 VSIX 프로젝트 바로 가기 메뉴에서 **시작 프로젝트로 설정**을 선택합니다.

4. **source.extension.vsixmanifest**에서 제스처 처리기 클래스 라이브러리 프로젝트를 MEF 구성 요소로 추가합니다.

    1. **메타데이터** 탭에서 VSIX 이름을 설정합니다.

    2. **설치 대상** 탭에서 Visual Studio 버전을 대상으로 설정합니다.

    3. **자산** 탭에서 **새로 만들기**를 선택하고 대화 상자에서 다음을 설정합니다.

         **유형**  =  **MEF 구성 요소**

         **원본**  =  **현재 솔루션의 프로젝트**

         **프로젝트**  =  *클래스 라이브러리 프로젝트*

## <a name="executing-the-gesture-handler"></a><a name="Executing"></a> 제스처 처리기 실행
 테스트를 위해 디버그 모드에서 제스처 처리기를 실행합니다.

#### <a name="to-test-the-gesture-handler"></a>제스처 처리기를 테스트하려면

1. **F5**키를 누르거나, **디버그** 메뉴에서 **디버깅 시작**을 클릭합니다.

    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 의 실험적 인스턴스가 시작됩니다.

    **문제 해결**: 새 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 가 시작되지 않는 경우:

   - 프로젝트가 두 개 이상 있으면 VSIX 프로젝트가 솔루션의 시작 프로젝트로 설정되었는지 확인합니다.

   - 솔루션 탐색기의 시작 또는 전용 프로젝트 바로 가기 메뉴에서 속성을 선택합니다. 프로젝트 속성 편집기에서 **디버그** 탭을 선택 합니다. **시작 외부 프로그램** 필드의 문자열이 보통 다음과 같은의 전체 경로 이름 인지 확인 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

        `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. 실험적 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 모델링 프로젝트를 열거나 만들고 모델링 다이어그램을 열거나 만듭니다. 제스처 처리기 클래스의 특성에 나열된 형식 중 하나에 속한 다이어그램을 사용합니다.

3. 다이어그램에서 아무 곳이나 두 번 클릭합니다. 두 번 클릭 처리기가 호출되어야 합니다.

4. 요소를 UML 탐색기에서 다이어그램으로 끌어 놓습니다. 끌기 처리기가 호출되어야 합니다.

   **문제 해결**: 제스처 처리기가 작동하지 않으면 다음을 확인합니다.

- 제스처 처리기 프로젝트는 VSIX 프로젝트에서 **source.extensions.manifest** 의 **자산** 탭에 MEF 구성 요소로 나열됩니다.

- 모든 `Import` 및 `Export` 특성의 매개 변수가 유효합니다.

- `CanDragDrop` 메서드가 `false`를 반환하지 않습니다.

- 사용 중인 모델 다이어그램 형식(UML 클래스, 시퀀스 등)은 제스처 처리기 클래스 특성 [ClassDesignerExtension], [SequenceDesignerExtension] 등의 하나로 나열됩니다.

- 이 형식의 대상 및 삭제된 요소에 대해 정의된 기본 제공 기능이 없습니다.

## <a name="implementing-the-gesture-handler"></a><a name="Implementing"></a> 제스처 처리기 구현

### <a name="the-gesture-handler-methods"></a>제스처 처리기 메서드
 제스처 처리기 클래스는 <xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement.IGestureExtension>을 구현하고 내보냅니다. 정의해야 하는 메서드는 다음과 같습니다.

|서명|Description|
|-|-|
|`bool CanDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|이 대상에서 삭제될 `true` 에서 참조되는 소스 요소를 허용하려면 `dragEvent` 를 반환합니다.<br /><br /> 이 메서드는 모델을 변경하면 안 됩니다. 사용자가 마우스를 이동할 때 화살표 상태를 결정하는 데 사용되므로 빠르게 작동해야 합니다.|
|`void OnDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|`dragEvent`에서 참조되는 소스 개체 및 대상에 따라 모델을 업데이트합니다.<br /><br /> 사용자가 마우스를 끌고 나서 놓을 때 호출됩니다.|
|`void OnDoubleClick (ShapeElement target, DiagramPointEventArgs pointEvent)`|`target`은 사용자가 두 번 클릭한 모양입니다.|

 UML뿐만 아니라 .NET 클래스 뷰의 파일, 노드와 같은 다양한 다른 항목을 허용할 수 있는 처리기를 작성할 수 있습니다. 항목의 serialize된 형식을 디코딩할 수 있는 `OnDragDrop` 메서드를 작성한 경우 사용자가 이들 항목을 UML 다이어그램으로 끌 수 있습니다. 디코딩 방법은 항목 형식에 따라 달라집니다.

 메서드의 매개 변수는 다음과 같습니다.

- `ShapeElement target`. 사용자가 항목을 끌어온 모양 또는 다이어그램.

    `ShapeElement`는 UML 모델링 도구의 기반이 되는 구현의 클래스입니다. UML 모델 및 다이어그램이 불일치 상태로 전환되는 위험을 줄이려면 이 클래스의 메서드를 직접 사용하지 않는 것이 좋습니다. 대신에서 요소를 래핑하고 `IShape` [다이어그램에 UML 모델 표시](../modeling/display-a-uml-model-on-diagrams.md)에 설명 된 메서드를 사용 합니다.

  - `IShape`를 가져오려면

      ```
      IShape targetIShape = target.CreateIShape(target);
      ```

  - 끌기 또는 두 번 클릭 작업으로 대상으로 지정된 모델 요소를 가져오려면

      ```
      IElement target = targetIShape.Element;
      ```

      이를 더 구체적인 형식의 요소로 캐스팅할 수 있습니다.

  - UML 모델이 포함된 UML 모델 저장소를 가져오려면

      ```
      IModelStore modelStore =
        targetIShape.Element.GetModelStore(); 
      ```

  - 호스트 및 서비스 공급자에 대한 액세스 권한을 얻으려면

      ```
      target.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE
      ```

- `DiagramDragEventArgs eventArgs`. 이 매개 변수는 끌기 작업의 소스 개체에 대한 serialize된 형식을 전달합니다.

    ```
    System.Windows.Forms.IDataObject data = eventArgs.Data;
    ```

     다양한 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]파트 또는 Windows 바탕 화면에서 다양한 종류의 요소를 다이어그램으로 끌 수 있습니다. `IDataObject`에서 다양한 형식의 요소가 다양한 방법으로 인코드됩니다. 요소를 추출하려면 해당 개체 형식에 대한 설명서를 참조하세요.

     원본 개체가 UML 모델 탐색기 또는 다른 UML 다이어그램에서 끌어온 UML 요소인 경우 [IDataObject에서 uml 모델 요소 가져오기](../modeling/get-uml-model-elements-from-idataobject.md)를 참조 하세요.

### <a name="writing-the-code-of-the-methods"></a>메서드 코드 작성
 모델을 읽고 업데이트하는 코드를 작성하는 방법에 대한 자세한 내용은 [Programming with the UML API](../modeling/programming-with-the-uml-api.md)을 참조하세요.

 끌기 작업에서 모델 정보에 액세스 하는 방법에 대 한 자세한 내용은 [IDataObject에서 UML 모델 요소 가져오기](../modeling/get-uml-model-elements-from-idataobject.md)를 참조 하세요.

 시퀀스 다이어그램을 처리 하는 경우 [UML API를 사용 하 여 uml 시퀀스 다이어그램 편집](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)을 참조 하세요.

 메서드의 매개 변수 이외에 현재 다이어그램 및 모델에 대한 액세스를 제공하는 클래스에서 가져온 속성을 선언할 수도 있습니다.

```
[Import] public IDiagramContext DiagramContext { get; set; }
```

 `IDiagramContext` 선언을 사용하여 메서드에서 다이어그램, 현재 선택 영역 및 모델에 액세스하는 코드를 작성할 수 있습니다.

```
IDiagram diagram = this.DiagramContext.CurrentDiagram;
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>)
{ IElement element = shape.Element; ... }
IModelStore modelStore = diagram.ModelStore;
IModel model = modelStore.Root;
foreach (IDiagram diagram in modelStore.Diagrams) {...}
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}
```

 자세한 내용은 [UML 모델 탐색](../modeling/navigate-the-uml-model.md)을 참조 하세요.

## <a name="installing-and-uninstalling-an-extension"></a><a name="Installing"></a> 확장 설치 및 제거
 사용 중인 컴퓨터 및 다른 컴퓨터에서 모두 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 확장을 설치할 수 있습니다.

#### <a name="to-install-an-extension"></a>확장을 설치하려면

1. 사용 중인 컴퓨터에서 VSIX 프로젝트를 통해 빌드된 **.vsix** 파일을 찾습니다.

    1. **솔루션 탐색기**의 VSIX 프로젝트 바로 가기 메뉴에서 **Windows 탐색기에서 폴더 열기**를 선택합니다.

    2. 파일 ** \\ \* bin \\ **_을 찾습니다_**. vsix**

2. 확장을 설치할 대상 컴퓨터에 **.vsix** 파일을 복사합니다. 이 컴퓨터는 사용 중인 컴퓨터이거나 다른 컴퓨터일 수 있습니다.

     대상 컴퓨터에는 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **source.extension.vsixmanifest**에서 지정한 버전 중 하나가 있어야 합니다.

3. 대상 컴퓨터에서 **.vsix** 파일을 엽니다.

     **Visual Studio 확장 설치 관리자** 에서 확장을 열고 설치합니다.

4. [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]를 시작하거나 다시 시작합니다.

#### <a name="to-uninstall-an-extension"></a>확장을 제거하려면

1. **도구** 메뉴 모음에서 **확장 및 업데이트**를 선택합니다.

2. **설치된 확장**을 확장합니다.

3. 확장을 선택하고 **제거**를 선택합니다.

   드물게 결함이 있는 확장은 로드되지 않고 오류 창에 보고서를 생성하지만 확장 관리자에 나타나지 않습니다. 이 경우 다음 위치에서 파일을 삭제하여 확장을 제거할 수 있습니다.

   *% LocalAppData%* **\Local\Microsoft\VisualStudio \\ [version] \extensions**

## <a name="example"></a><a name="DragExample"></a> 예제
 다음 샘플에서는 구성 요소 다이어그램에서 끌어온 구성 요소의 파트 및 포트를 기반으로 시퀀스 다이어그램에서 수명선을 만드는 방법을 보여 줍니다.

 테스트하려면 F5 키를 누릅니다. Visual Studio의 실험적 인스턴스가 열립니다. 이 인스턴스에서 UML 모델을 열고 구성 요소 다이어그램에 구성 요소를 만듭니다. 이 구성 요소에 몇몇 인터페이스 및 내부 구성 요소 파트를 추가합니다. 인터페이스 및 파트를 선택합니다. 그다음에 인터페이스 및 파트를 시퀀스 다이어그램으로 끕니다. (구성 요소 다이어그램에서 시퀀스 다이어그램에 대 한 탭까지 끌어 오고 차례로 시퀀스 다이어그램으로 이동 합니다.) 각 인터페이스와 파트에 대 한 수명선이 표시 됩니다.

 시퀀스 다이어그램에 상호 작용을 바인딩하는 방법에 대 한 자세한 내용은 [UML API를 사용 하 여 uml 시퀀스 다이어그램 편집](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)을 참조 하세요.

```
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.Uml.Interactions;
using Microsoft.VisualStudio.Uml.CompositeStructures;
using Microsoft.VisualStudio.Uml.Components;

/// <summary>
/// Creates lifelines from component ports and parts.
/// </summary>
[Export(typeof(IGestureExtension))]
[SequenceDesignerExtension]
public class CreateLifelinesFromComponentParts : IGestureExtension
{
  [Import]
  public IDiagramContext Context { get; set; }

  /// <summary>
  /// Called by the modeling framework when
  /// the user drops something on a target.
  /// </summary>
  /// <param name="target">The target shape or diagram </param>
  /// <param name="dragEvent">The item being dragged</param>
  public void OnDragDrop(ShapeElement target,
           DiagramDragEventArgs dragEvent)
  {
    ISequenceDiagram diagram = Context.CurrentDiagram
            as ISequenceDiagram;
    IInteraction interaction = diagram.Interaction;
    if (interaction == null)
    {
      // Sequence diagram is empty: create an interaction.
      interaction = diagram.ModelStore.Root.CreateInteraction();
      interaction.Name = Context.CurrentDiagram.Name;
      diagram.Bind(interaction);
    }
    foreach (IConnectableElement connectable in
       GetConnectablesFromDrag(dragEvent))
    {
      ILifeline lifeline = interaction.CreateLifeline();
      lifeline.Represents = connectable;
      lifeline.Name = connectable.Name;
    }
  }

  /// <summary>
  /// Called by the modeling framework to determine whether
  /// the user can drop something on a target.
  /// Must not change anything.
  /// </summary>
  /// <param name="target">The target shape or diagram</param>
  /// <param name="dragEvent">The item being dragged</param>
  /// <returns>true if this item can be dropped on this target</returns>
  public bool CanDragDrop(ShapeElement target,
           DiagramDragEventArgs dragEvent)
  {
    IEnumerable<IConnectableElement> connectables = GetConnectablesFromDrag(dragEvent);
    return connectables.Count() > 0;
  }

  ///<summary>
  /// Get dragged parts and ports of an IComponent.
  ///</summary>
  private IEnumerable<IConnectableElement>
    GetConnectablesFromDrag(DiagramDragEventArgs dragEvent)
  {
    foreach (IElement element in
      GetModelElementsFromDragEvent(dragEvent))
    {
      IConnectableElement part = element as IConnectableElement;
      if (part != null)
      {
        yield return part;
      }
    }
  }

  /// <summary>
  /// Retrieves UML IElements from drag arguments.
  /// Works for drags from UML diagrams.
  /// </summary>
  private IEnumerable<IElement> GetModelElementsFromDragEvent
          (DiagramDragEventArgs dragEvent)
  {
    //ElementGroupPrototype is the container for
    //dragged and copied elements and toolbox items.
    ElementGroupPrototype prototype =
       dragEvent.Data.
       GetData(typeof(ElementGroupPrototype))
            as ElementGroupPrototype;
    // Locate the originals in the implementation store.
    IElementDirectory implementationDirectory =
       dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;

    return prototype.ProtoElements.Select(
      prototypeElement =>
      {
        ModelElement element = implementationDirectory
          .FindElement(prototypeElement.ElementId);
        ShapeElement shapeElement = element as ShapeElement;
        if (shapeElement != null)
        {
          // Dragged from a diagram.
          return shapeElement.ModelElement as IElement;
        }
        else
        {
          // Dragged from UML Model Explorer.
          return element as IElement;
        }
      });
  }

  public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
  {
  }
}

```

 의 코드는 `GetModelElementsFromDragEvent()` [IDATAOBJECT에서 UML 모델 요소 가져오기](../modeling/get-uml-model-elements-from-idataobject.md)에 설명 되어 있습니다.

## <a name="see-also"></a>관련 항목
 [모델링 확장 정의 및 설치](../modeling/define-and-install-a-modeling-extension.md) [uml 모델 및 다이어그램 확장](../modeling/extend-uml-models-and-diagrams.md) [모델링 다이어그램에서 메뉴 명령 정의](../modeling/define-a-menu-command-on-a-modeling-diagram.md) uml [API를 사용 하 여 프로그래밍 하는](../modeling/programming-with-the-uml-api.md) [uml 모델에 대 한 유효성 검사 제약 조건 정의](../modeling/define-validation-constraints-for-uml-models.md)

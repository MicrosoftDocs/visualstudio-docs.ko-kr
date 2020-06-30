---
title: 모델링 다이어그램에서 메뉴 명령 정의 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, menu commands
ms.assetid: 79c277de-5871-4fc7-9701-55eec5c3cd46
caps.latest.revision: 63
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b6481a56b4cbc254baaee3ae087201df69c371b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534214"
---
# <a name="define-a-menu-command-on-a-modeling-diagram"></a>모델링 다이어그램의 메뉴 명령 정의
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 UML 다이어그램의 바로 가기 메뉴에 추가 메뉴 항목을 정의할 수 있습니다. 다이어그램에서 임의 요소의 바로 가기 메뉴에 메뉴 명령을 표시하고 사용하도록 설정할지 여부를 제어할 수 있으며, 사용자가 메뉴 항목을 선택할 때 실행되는 코드를 작성할 수 있습니다. 이러한 확장을[VSIX](https://msdn.microsoft.com/library/dd393694(VS.100).aspx)(Visual Studio Integration Extension)로 패키징하고 다른 Visual Studio 사용자에게 배포할 수 있습니다.

## <a name="requirements"></a>요구 사항
 [요구 사항](../modeling/extend-uml-models-and-diagrams.md#Requirements)을 참조 하세요.

 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

## <a name="defining-the-menu-command"></a>메뉴 명령 정의
 UML 디자이너에 대한 메뉴 명령을 만들려면 명령의 동작을 정의하는 클래스를 만들고 해당 클래스를 VSIX(Visual Studio Integration Extension)에 포함해야 합니다. VSIX는 명령을 설치할 수 있는 컨테이너 역할을 합니다. 메뉴 명령을 정의하는 대신 다음 두 가지 방법을 사용할 수 있습니다.

- **프로젝트 템플릿을 사용하여 자체 VSIX에서 메뉴 명령을 만듭니다.** 이는 더 빠른 방법입니다. 메뉴 명령을 유효성 검사 확장, 사용자 지정 도구 상자 또는 제스처 처리기와 같은 다른 형식 확장과 결합하지 않으려면 이 방법을 사용합니다.

- **별도의 메뉴 명령 및 VSIX 프로젝트를 만듭니다.** 여러 확장 형식을 같은 VSIX로 결합하려면 이 방법을 사용합니다. 예를 들어 메뉴 명령에서 모델이 특정 제약 조건을 따르도록 요구하면 유효성 검사 방법과 동일한 VSIX에 해당 제스처 처리기를 포함할 수 있습니다.

#### <a name="to-create-a-menu-command-in-its-own-vsix"></a>자체 VSIX에 메뉴 명령을 만들려면

1. **새 프로젝트** 대화 상자의 **모델링 프로젝트**에서 **명령 확장**을 선택합니다.

2. 새 프로젝트에서 **.cs** 파일을 열고 `CommandExtension` 클래스를 수정하여 명령을 구현합니다.

    자세한 내용은 [메뉴 명령 구현](#Implementing)을 참조하세요.

3. 새 클래스를 정의하여 이 프로젝트에 다른 명령을 추가할 수 있습니다.

4. F5 키를 눌러 메뉴 명령을 테스트합니다. 자세한 내용은 [메뉴 명령 실행](#Executing)을 참조하세요.

5. 프로젝트에서 빌드된 파일 **bin \\ \* \\ \* . vsix** 를 복사 하 여 다른 컴퓨터에 메뉴 명령을 설치 합니다. 자세한 내용은 [확장 설치 및 제거](#Installing)를 참조하세요.

   다음은 대체 절차입니다.

#### <a name="to-create-a-menu-command-in-a-separate-class-library-dll-project"></a>별도 클래스 라이브러리(DLL) 프로젝트에서 메뉴 명령을 만들려면

1. 새 Visual Studio 솔루션이나 기존 솔루션에서 클래스 라이브러리 프로젝트를 만듭니다.

   1. **파일** 메뉴에서 **새로 만들기**, **프로젝트**를 차례로 선택합니다.

   2. **설치된 템플릿**아래에서 **Visual C#** 또는 **Visual Basic**을 선택합니다. 가운데 열에서 **클래스 라이브러리**를 선택합니다.

   3. **솔루션** 을 설정하여 새 솔루션을 만들지 또는 열려 있는 VSIX 솔루션에 구성 요소를 추가할지를 나타냅니다.

   4. 프로젝트 이름 및 위치를 설정하고 확인을 클릭합니다.

2. 프로젝트에 다음 참조를 추가합니다.

   |                                                                                                    참조                                                                                                    |                                                                                                  수행할 수 있는 기능                                                                                                  |
   |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                                                                                        System.ComponentModel.Composition                                                                                        |                                         [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)를 사용하여 구성 요소를 정의합니다.                                          |
   |                                                                                      Microsoft.VisualStudio.Uml.Interfaces                                                                                      |                                                                                        모델 요소의 속성을 읽고 변경합니다.                                                                                         |
   |                                                                             Microsoft.VisualStudio.ArchitectureTools.Extensibility                                                                              |                                                                                      다이어그램에서 모델 요소를 만들고 모양을 수정합니다.                                                                                       |
   |                                                                                  Microsoft.VisualStudio.Modeling.Sdk.[version]                                                                                  | 모델 이벤트 처리기를 정의합니다.<br /><br /> 모델에 대한 일련의 변경 내용을 캡슐화합니다. 자세한 내용은 [트랜잭션을 사용 하 여 UML 모델 업데이트 링크](../modeling/link-uml-model-updates-by-using-transactions.md)를 참조 하세요. |
   |                                                            Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]<br /><br /> (항상 필수는 아님)                                                             |                                                                                   제스처 처리기에 대한 추가 다이어그램 요소에 액세스합니다.                                                                                   |
   | Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer<br /><br /> 레이어 다이어그램의 명령에만 필요합니다. 자세한 내용은 [레이어 다이어그램 확장](../modeling/extend-layer-diagrams.md)을 참조 하세요. |                                                                                             레이어 다이어그램의 명령을 정의합니다.                                                                                              |

3. 프로젝트에 클래스 파일을 추가하고 해당 콘텐츠를 다음 코드로 설정합니다.

   > [!NOTE]
   > 네임스페이스, 클래스 이름 및 `Text` 에서 반환되는 값을 원하는 대로 변경합니다.
   >
   >  여러 명령을 정의하는 경우 클래스 이름의 사전순으로 메뉴에 나타납니다.

   ```
   using System.ComponentModel.Composition;
   using System.Linq;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;
   using Microsoft.VisualStudio.Uml.Classes;
       // ADD other UML namespaces if required

   namespace UMLmenu1 // CHANGE
   {
     // DELETE any of these attributes if the command
     // should not appear in some types of diagram.
     [ClassDesignerExtension]
     [ActivityDesignerExtension]
     [ComponentDesignerExtension]
     [SequenceDesignerExtension]
     [UseCaseDesignerExtension]
     // [LayerDesignerExtension]

     // All menu commands must export ICommandExtension:
     [Export (typeof(ICommandExtension))]
     // CHANGE class name – determines order of appearance on menu:
     public class Menu1 : ICommandExtension
     {
       [Import]
       public IDiagramContext DiagramContext { get; set; }

       public void QueryStatus(IMenuCommand command)
       { // Set command.Visible or command.Enabled to false
         // to disable the menu command.
         command.Visible = command.Enabled = true;
       }

       public string Text
       {
         get { return "MENU COMMAND LABEL"; }
       }

       public void Execute(IMenuCommand command)
       {
         // A selection of starting points:
         IDiagram diagram = this.DiagramContext.CurrentDiagram;
         foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())
         { IElement element = shape.Element; }
         IModelStore modelStore = diagram.ModelStore;
         IModel model = modelStore.Root;
         foreach (IElement element in modelStore.AllInstances<IClass>())
         { }
       }
     }
   }
   ```

    메서드에 삽입할 항목에 대한 자세한 내용은 [메뉴 명령 구현](#Implementing)을 참조하세요.

   명령을 설치할 컨테이너로 사용되는 VSIX 프로젝트에 메뉴 명령을 추가해야 합니다. 필요하면 같은 VSIX에 다른 구성 요소를 포함할 수 있습니다.

#### <a name="to-add-a-menu-command-to-a-vsix-project"></a>VSIX 프로젝트에 메뉴 명령을 추가하려면

1. 자체 VSIX를 사용하여 메뉴 명령을 만든 경우에는 이 절차가 필요하지 않습니다.

2. 솔루션에 VSIX 프로젝트가 없으면 VSIX 프로젝트를 만듭니다.

    1. **솔루션 탐색기**의 솔루션 바로 가기 메뉴에서 **추가**, **새 프로젝트**를 차례로 선택 합니다.

    2. **설치된 템플릿**에서 **Visual C#** 또는 **Visual Basic**을 확장한 다음 **확장성**을 선택합니다. 가운데 열에서 **VSIX 프로젝트**를 선택합니다.

3. 솔루션 탐색기의 VSIX 프로젝트 바로 가기 메뉴에서 **시작 프로젝트로 설정**을 선택합니다.

4. **source.extension.vsixmanifest**를 엽니다.

    1. **메타데이터** 탭에서 VSIX 이름을 설정합니다.

    2. **설치 대상** 탭에서 Visual Studio 버전을 대상으로 설정합니다.

    3. **자산** 탭에서 **새로 만들기**를 선택하고 대화 상자에서 다음을 설정합니다.

         **유형**  =  **MEF 구성 요소**

         **원본**  =  **현재 솔루션의 프로젝트**

         **프로젝트**  =  *클래스 라이브러리 프로젝트*

## <a name="implementing-the-menu-command"></a><a name="Implementing"></a>메뉴 명령 구현
 메뉴 명령 클래스는 <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension>에 필요한 메서드를 구현합니다.

|서명|설명|
|-|-|
|`string Text { get; }`|메뉴 항목의 레이블을 반환합니다.|
|`void QueryStatus(IMenuCommand command);`|사용자가 다이어그램을 마우스 오른쪽 단추로 클릭하면 호출됩니다.<br /><br /> 이 메서드는 모델을 변경하면 안 됩니다.<br /><br /> `DiagramContext.CurrentDiagram.SelectedShapes` 를 사용하여 명령을 표시하고 사용할 수 있도록 할지 여부를 결정합니다.<br /><br /> 다음과 같이 설정합니다.<br /><br /> -   `command.Visible``true`사용자가 다이어그램을 마우스 오른쪽 단추로 클릭할 때 명령이 메뉴에 표시 되어야 하는 경우<br />-   `command.Enabled``true`사용자가 메뉴에서 명령을 클릭할 수 있는 경우<br />-   `command.Text`메뉴 레이블을 동적으로 설정 하려면|
|`void Execute (IMenuCommand command);`|표시되고 사용할 수 있는 경우 사용자가 메뉴 항목을 클릭할 때 호출됩니다.|

### <a name="accessing-the-model-in-code"></a>코드에서 모델 액세스
 메뉴 명령 클래스에 다음 선언을 포함합니다.

```
[Import] public IDiagramContext DiagramContext { get; set; }
```

 ...

 `IDiagramContext` 선언을 사용하여 메서드에서 다이어그램, 현재 선택 영역 및 모델에 액세스하는 코드를 작성할 수 있습니다.

```
IDiagram diagram = this.DiagramContext.CurrentDiagram;
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())
{ IElement element = shape.Element; ... }
IModelStore modelStore = diagram.ModelStore;
IModel model = modelStore.Root;
foreach (IElement element in modelStore.AllInstances<IUseCase>()) {...}
```

### <a name="navigating-and-updating-the-model"></a>모델 탐색 및 업데이트
 UML 모델의 요소는 모두 API를 통해 사용할 수 있습니다. 현재 선택 영역이나 모델의 루트에서 다른 모든 요소에 액세스할 수 있습니다. 자세한 내용은 uml [모델 탐색](../modeling/navigate-the-uml-model.md) 및 [uml API를 사용한 프로그래밍](../modeling/programming-with-the-uml-api.md)을 참조 하세요.

 시퀀스 다이어그램을 처리 하는 경우 [UML API를 사용 하 여 uml 시퀀스 다이어그램 편집](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)을 참조 하세요.

 API를 통해 요소의 속성을 변경하고, 요소 및 관계를 삭제하고, 새 요소 및 관계를 만들 수도 있습니다.

 기본적으로 Execute 메서드의 각 변경 작업은 별도 트랜잭션에서 수행됩니다. 사용자가 각 변경 내용을 개별적으로 취소할 수 있습니다. 변경 내용을 단일 트랜잭션으로 그룹화 하려는 경우 <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoTransaction> [트랜잭션을 사용 하 여 UML 모델 업데이트 연결](../modeling/link-uml-model-updates-by-using-transactions.md)에 설명 된 대로을 사용 합니다.

### <a name="use-the-ui-thread-for-updates"></a>업데이트에 UI 스레드 사용
 백그라운드 스레드에서 모델을 업데이트하는 것이 유용한 경우도 있습니다. 예를 들어 명령이 속도가 느린 리소스에서 데이터를 로드하는 경우 작업이 진행되는 동안 사용자가 변경 내용을 보고 필요한 경우 작업을 취소할 수 있도록 백그라운드 스레드에서 로드를 수행할 수 있습니다.

 그러나 모델 저장소가 스레드로부터 안전하지 않은 것에 주의해야 합니다. 항상 UI(사용자 인터페이스) 스레드를 사용하여 업데이트해야 하며, 가능한 경우 백그라운드 작업이 진행되는 동안 사용자가 편집할 수 없도록 해야 합니다. 예제는 [백그라운드 스레드에서 UML 모델 업데이트](../modeling/update-a-uml-model-from-a-background-thread.md)를 참조 하세요.

## <a name="executing-the-menu-command"></a><a name="Executing"></a>메뉴 명령 실행
 테스트를 위해 디버그 모드에서 명령을 실행합니다.

#### <a name="to-test-the-menu-command"></a>메뉴 명령을 테스트하려면

1. **F5**키를 누르거나, **디버그** 메뉴에서 **디버깅 시작**을 선택합니다.

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 의 실험적 인스턴스가 시작됩니다.

     **문제 해결**: 새 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 가 시작되지 않는 경우:

    - 프로젝트가 두 개 이상 있으면 VSIX 프로젝트가 솔루션의 시작 프로젝트로 설정되었는지 확인합니다.

    - 솔루션 탐색기의 시작 또는 전용 프로젝트 바로 가기 메뉴에서 **속성**을 선택합니다. 프로젝트 속성 편집기에서 **디버그** 탭을 선택 합니다. **시작 외부 프로그램** 필드의 문자열이 보통 다음과 같은의 전체 경로 이름 인지 확인 합니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. 실험적 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 모델링 프로젝트를 열거나 만들고 모델링 다이어그램을 열거나 만듭니다. 메뉴 명령 클래스의 특성에 나열된 형식 중 하나에 속하는 다이어그램을 사용합니다.

3. 다이어그램에 있는 바로 가기 메뉴를 엽니다. 명령이 메뉴에 표시되어야 합니다.

     **문제 해결**: 명령이 메뉴에 표시되지 않는 경우 다음을 확인합니다.

    - 메뉴 명령 프로젝트가 VSIX 프로젝트에서 **source.extensions.manifest** 의 **자산** 탭에 MEF 구성 요소로 나열됩니다.

    - `Import` 및 `Export` 특성의 매개 변수가 유효합니다.

    - `QueryStatus`메서드가를 설정 하지 않습니다 `command` .`Enabled` 또는 `Visible` 필드를로 변환할 수 `false` 있습니다.

    - 사용 중인 모델 다이어그램 형식(UML 클래스, 시퀀스 등)이 메뉴 명령 클래스 특성 `[ClassDesignerExtension]`, `[SequenceDesignerExtension]` 등의 하나로 나열됩니다.

## <a name="installing-and-uninstalling-an-extension"></a><a name="Installing"></a>확장 설치 및 제거
 사용 중인 컴퓨터 및 다른 컴퓨터에서 모두 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 확장을 설치할 수 있습니다.

#### <a name="to-install-an-extension"></a>확장을 설치하려면

1. 사용 중인 컴퓨터에서 VSIX 프로젝트를 통해 빌드된 **.vsix** 파일을 찾습니다.

    1. **솔루션 탐색기**의 VSIX 프로젝트 바로 가기 메뉴에서 **Windows 탐색기에서 폴더 열기**를 선택합니다.

    2. 파일 ** \\ \* bin \\ **_을 찾습니다_**. vsix**

2. 확장을 설치할 대상 컴퓨터에 **.vsix** 파일을 복사합니다. 이 컴퓨터는 사용 중인 컴퓨터이거나 다른 컴퓨터일 수 있습니다.

     대상 컴퓨터에는 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **source.extension.vsixmanifest**에서 지정한 버전 중 하나가 있어야 합니다.

3. 대상 컴퓨터에서 **.vsix** 파일을 두 번 클릭하여 엽니다.

     **Visual Studio 확장 설치 관리자** 에서 확장을 열고 설치합니다.

4. [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]를 시작하거나 다시 시작합니다.

#### <a name="to-uninstall-an-extension"></a>확장을 제거하려면

1. **도구** 메뉴 모음에서 **확장 및 업데이트**를 선택합니다.

2. **설치된 확장**을 확장합니다.

3. 확장을 선택하고 **제거**를 선택합니다.

   드물게 결함이 있는 확장은 로드되지 않고 오류 창에 보고서를 생성하지만 확장 관리자에 나타나지 않습니다. 이 경우 다음 위치에서 파일을 삭제하여 확장을 제거할 수 있습니다.

   *% LocalAppData%* **\Local\Microsoft\VisualStudio \\ [version] \extensions**

## <a name="example"></a><a name="MenuExample"></a> 예
 다음 예제에서는 클래스 다이어그램에서 두 요소의 이름은 교환하는 메뉴 명령에 대한 코드를 보여 줍니다. 이 코드는 이전 섹션에서 설명한 대로 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 확장 프로젝트로 빌드 및 설치해야 합니다.

```
using System.Collections.Generic; // for IEnumerable
using System.ComponentModel.Composition;
  // for [Import], [Export]
using System.Linq; // for IEnumerable extensions
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
  // for IDiagramContext
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
  // for designer extension attributes
using Microsoft.VisualStudio.Modeling.Diagrams;
  // for ShapeElement
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
  // for IGestureExtension, ICommandExtension, ILinkedUndoContext
using Microsoft.VisualStudio.Uml.Classes;
  // for class diagrams, packages

/// <summary>
/// Extension to swap names of classes in a class diagram.
/// </summary>
namespace SwapClassNames
{
  // Declare the class as an MEF component:
  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  // Add more ExportMetadata attributes to make
  // the command appear on diagrams of other types.
  public class NameSwapper : ICommandExtension
  {
  // MEF required interfaces:
  [Import]
  public IDiagramContext Context { get; set; }
  [Import]
  public ILinkedUndoContext LinkedUndoContext { get; set; }

  /// <summary>
  /// Swap the names of the currently selected elements.
  /// </summary>
  /// <param name="command"></param>
  public void Execute(IMenuCommand command)
  {
    // Get selected shapes that are IClassifiers -
    // IClasses, IInterfaces, IEnumerators.
    var selectedShapes = Context.CurrentDiagram
     .GetSelectedShapes<IClassifier>();
    if (selectedShapes.Count() < 2) return;

    // Get model elements displayed by shapes.
    IClassifier firstElement = selectedShapes.First().Element;
    IClassifier lastElement = selectedShapes.Last().Element;

    // Do the swap in a transaction so that user
    // cannot undo one change without the other.
    using (ILinkedUndoTransaction transaction =
    LinkedUndoContext.BeginTransaction("Swap names"))
    {
    string firstName = firstElement.Name;
    firstElement.Name = lastElement.Name;
    lastElement.Name = firstName;
    transaction.Commit();
    }
  }

  /// <summary>
  /// Called by Visual Studio to determine whether
  /// menu item should be visible and enabled.
  /// </summary>
  public void QueryStatus(IMenuCommand command)
  {
    int selectedClassifiers = Context.CurrentDiagram
     .GetSelectedShapes<IClassifier>().Count();
    command.Visible = selectedClassifiers > 0;
    command.Enabled = selectedClassifiers == 2;
  }

  /// <summary>
  /// Name of the menu command.
  /// </summary>
  public string Text
  {
    get { return "Swap Names"; }
  }
  }

}
```

## <a name="see-also"></a>참고 항목
 [모델링 확장 정의 및 설치](../modeling/define-and-install-a-modeling-extension.md) [uml 모델 및 다이어그램 확장](../modeling/extend-uml-models-and-diagrams.md) [모델링 다이어그램에서 제스처 처리기 정의](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) [사용자 지정 모델링 도구 상자 항목 정의](../modeling/define-a-custom-modeling-toolbox-item.md) uml [모델에 대 한 유효성 검사 제약 조건 정의](../modeling/define-validation-constraints-for-uml-models.md) uml api를 사용한 uml api [프로그래밍](../modeling/programming-with-the-uml-api.md) 을 [사용 하 여 uml 시퀀스 다이어그램 편집](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)
 
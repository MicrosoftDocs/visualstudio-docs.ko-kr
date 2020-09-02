---
title: MEF를 사용하여 DSL 확장
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04d14b3b17953ef30620d9f616bb471b186e9c9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547643"
---
# <a name="extend-your-dsl-by-using-mef"></a>MEF를 사용하여 DSL 확장

Managed Extensibility Framework (MEF)를 사용 하 여 DSL (도메인 특정 언어)을 확장할 수 있습니다. 사용자 또는 다른 개발자는 DSL 정의 및 프로그램 코드를 변경 하지 않고도 DSL 용 확장을 작성할 수 있습니다. 이러한 확장에는 메뉴 명령, 끌어서 놓기 처리기 및 유효성 검사가 포함 됩니다. 사용자는 DSL을 설치한 다음 필요에 따라 확장을 설치할 수 있습니다.

또한 dsl에서 MEF를 사용 하도록 설정 하면 dsl을 사용 하는 경우 dsl의 기능 중 일부를 작성 하는 것이 더 쉬울 수 있습니다.

MEF에 대 한 자세한 내용은 [Managed Extensibility Framework (mef)](/dotnet/framework/mef/index)를 참조 하세요.

### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>MEF에서 DSL을 확장할 수 있도록 설정 하려면

1. **Dslpackage** 프로젝트 내에 **mefextension** 이라는 새 폴더를 만듭니다. 다음 파일을 추가 합니다.

     파일 이름: `CommandExtensionVSCT.tt`

    > [!IMPORTANT]
    > 이 파일의 GUID를 DslPackage\GeneratedCode\Constants.tt에 정의 된 GUID CommandSetId와 동일 하 게 설정 합니다.

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#
    // CmdSet Guid must be defined before master template is included
    // This Guid must be kept synchronized with the CommandSetId Guid in Constants.tt
    Guid guidCmdSet = new Guid ("00000000-0000-0000-0000-000000000000");
    string menuidCommandsExtensionBaseId="0x4000";
    #>
    <#@ include file="DslPackage\CommandExtensionVSCT.tt" #>
    ```

    파일 이름: `CommandExtensionRegistrar.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\CommandExtensionRegistrar.tt" #>
    ```

    파일 이름: `ValidationExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionEnablement.tt" #>
    ```

    파일 이름: `ValidationExtensionRegistrar.tt`

    이 파일을 추가 하는 경우 DSL 탐색기의 **Editorvalidation** 에서 하나 이상의 스위치를 사용 하 여 dsl에서 유효성 검사를 사용 하도록 설정 해야 합니다.

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>
    ```

    파일 이름: `PackageExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>
    ```

2. **Dsl** 프로젝트 내에 **mefextension** 이라는 새 폴더를 만듭니다. 다음 파일을 추가 합니다.

     파일 이름: `DesignerExtensionMetaDataAttribute.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\DesignerExtensionMetadataAttribute.tt" #>
    ```

    파일 이름: `GestureExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionEnablement.tt" #>
    ```

    파일 이름: `GestureExtensionController.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionController.tt" #>
    ```

3. **DslPackage\Commands.vsct**라는 기존 파일에 다음 줄을 추가 합니다.

    ```xml
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>
    ```

    기존 지시문 뒤에 줄을 삽입 `<Include>` 합니다.

4. *Dsldefinition. dsl*을 엽니다.

5. DSL 탐색기에서 **Editor\validation**을 선택 합니다.

6. 속성 창에서 **사용 하** 는 속성 중 하나 이상이 인지 확인 합니다 `true` .

7. **솔루션 탐색기** 도구 모음에서 **모든 템플릿 변환**을 클릭 합니다.

     자회사 파일은 추가한 각 파일 아래에 나타납니다.

8. 솔루션을 빌드 및 실행 하 여 계속 작동 하는지 확인 합니다.

이제 DSL이 사용 됩니다. 메뉴 명령, 제스처 처리기 및 유효성 검사 제약 조건을 MEF 확장으로 작성할 수 있습니다. DSL 솔루션에서 다른 사용자 지정 코드와 함께 이러한 확장을 작성할 수 있습니다. 또한 사용자 또는 다른 개발자가 DSL을 확장 하는 별도의 Visual Studio 확장을 작성할 수 있습니다.

## <a name="create-an-extension-for-a-mef-enabled-dsl"></a>MEF 사용 DSL에 대 한 확장 만들기

직접 만든 MEF 지원 DSL에 대 한 액세스 권한이 있는 경우이를 위한 확장을 작성할 수 있습니다. 확장은 메뉴 명령, 제스처 처리기 또는 유효성 검사 제약 조건을 추가 하는 데 사용할 수 있습니다. 이러한 확장을 작성 하려면 VSIX (Visual Studio extension) 솔루션을 사용 합니다. 이 솔루션에는 두 부분, 즉 코드 어셈블리를 빌드하는 클래스 라이브러리 프로젝트와 어셈블리를 패키지 하는 VSIX 프로젝트가 있습니다.

### <a name="to-create-a-dsl-extension-vsix"></a>DSL 확장 VSIX를 만들려면

1. 새 **클래스 라이브러리** 프로젝트를 만듭니다.

2. 새 프로젝트에서 DSL의 어셈블리에 대 한 참조를 추가 합니다.

   - 이 어셈블리의 이름은 일반적으로 ".Dsl.dll"로 끝납니다.

   - DSL 프로젝트에 액세스할 수 있는 경우 디렉터리 **dsl \\ bin \\ \* ** 에서 어셈블리 파일을 찾을 수 있습니다.

   - DSL VSIX 파일에 액세스할 수 있는 경우 VSIX 파일의 파일 이름 확장명을 ".zip"으로 변경 하 여 어셈블리를 찾을 수 있습니다. .Zip 파일의 압축을 해제 합니다.

3. 다음 .NET 어셈블리에 대 한 참조를 추가 합니다.

   - Microsoft.VisualStudio.Modeling.Sdk.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll

   - System.ComponentModel.Composition.dll

   - System.Windows.Forms.dll

4. 새 **VSIX 프로젝트** 프로젝트를 만듭니다.

5. **솔루션 탐색기**에서 VSIX 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **시작 프로젝트로 설정**을 선택 합니다.

6. 새 프로젝트에서 **source.extension.vsixmanifest**를 엽니다.

7. **콘텐츠 추가**를 클릭 합니다. 대화 상자에서 **콘텐츠 형식** 을 **MEF 구성 요소**로 설정 하 고 **소스 프로젝트** 를 클래스 라이브러리 프로젝트로 설정 합니다.

8. DSL에 VSIX 참조를 추가 합니다.

   1. Source.extension.vsixmanifest에서 **참조 추가** 를 클릭 **합니다.**

   2. 대화 상자에서 **페이로드 추가** 를 클릭 한 다음 DSL의 VSIX 파일을 찾습니다. VSIX 파일은 DSL 솔루션의 **Dslpackage \\ bin \\ \* **에 빌드됩니다.

       이를 통해 사용자는 DSL 및 확장을 동시에 설치할 수 있습니다. 사용자가 이미 DSL을 설치한 경우에는 확장만 설치 됩니다.

9. **Source.extension.vsixmanifest**의 다른 필드를 검토 하 고 업데이트 합니다. **버전 선택** 을 클릭 하 고 올바른 Visual Studio 버전이 설정 되어 있는지 확인 합니다.

10. 클래스 라이브러리 프로젝트에 코드를 추가 합니다. 다음 섹션의 예제를 가이드로 사용 합니다.

     원하는 수의 명령, 제스처 및 유효성 검사 클래스를 추가할 수 있습니다.

11. 확장을 테스트 하려면 **f5**키를 누릅니다. Visual Studio의 실험적 인스턴스에서 DSL의 예제 파일을 만들거나 엽니다.

## <a name="writing-mef-extensions-for-dsls"></a>Dsl 용 MEF 확장 작성

별도의 DSL 확장 솔루션의 어셈블리 코드 프로젝트에 확장을 작성할 수 있습니다. DSL의 일부로 명령, 제스처 및 유효성 검사 코드를 작성 하는 편리한 방법인 DslPackage 프로젝트에서 MEF를 사용할 수도 있습니다.

### <a name="menu-commands"></a>메뉴 명령

메뉴 명령을 작성 하려면를 구현 하는 클래스를 정의 하 <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> 고 dsl에 정의 된 특성 ( *dsl*이라고 명명 됨)을 사용 하 여 클래스에 접두사를 지정 합니다 `CommandExtension` . 둘 이상의 메뉴 명령 클래스를 작성할 수 있습니다.

`QueryStatus()` 는 사용자가 다이어그램을 마우스 오른쪽 단추로 클릭할 때마다 호출 됩니다. 현재 선택 영역을 검사 하 고 `command.Enabled` 명령이 적용 되는 시점을 나타내도록 설정 해야 합니다.

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl; // My DSL
using Company.MyDsl.ExtensionEnablement; // My DSL
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement; // IVsSelectionContext
using Microsoft.VisualStudio.Modeling.ExtensionEnablement; // ICommandExtension

namespace MyMefExtension
{
  // Defined in Dsl\MefExtension\DesignerExtensionMetaDataAttribute.cs:
  [MyDslCommandExtension]
  public class MyCommandClass : ICommandExtension
  {
    /// <summary>
    /// Provides access to current document and selection.
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Called when the user selects this command.
    /// </summary>
    /// <param name="command"></param>
    public void Execute(IMenuCommand command)
    {
      // Transaction is required if you want to update elements.
      using (Transaction t = SelectionContext.CurrentStore
              .TransactionManager.BeginTransaction("fix names"))
      {
        foreach (ExampleShape shape in SelectionContext.CurrentSelection)
        {
          ExampleElement element = shape.ModelElement as ExampleElement;
          element.Name = element.Name + " !";
        }
        t.Commit();
      }
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines whether the command should appear.
    /// This method should set command.Enabled and command.Visible.
    /// </summary>
    /// <param name="command"></param>
    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled =
        command.Visible = (SelectionContext.CurrentSelection.OfType<ExampleShape>().Count() > 0);
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines the text of the command in the menu.
    /// </summary>
    public string Text
    {
      get { return "My menu command"; }
    }
  }
}
```

### <a name="gesture-handlers"></a>제스처 처리기

제스처 처리기는 Visual Studio 내부 또는 외부 어디에서 나 다이어그램으로 끌어 온 개체를 처리할 수 있습니다. 다음 예제에서는 사용자가 Windows 탐색기에서 다이어그램으로 파일을 끌어 놓을 수 있도록 합니다. 파일 이름을 포함 하는 요소를 만듭니다.

다른 DSL 모델 및 UML 모델의 끌기를 처리 하는 처리기를 작성할 수 있습니다. 자세한 내용은 [방법: 끌어서 놓기 처리기 추가](../modeling/how-to-add-a-drag-and-drop-handler.md)를 참조 하세요.

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace MefExtension
{
  [MyDslGestureExtension]
  class MyGestureExtension : IGestureExtension
  {
    public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
    {
      System.Windows.Forms.MessageBox.Show("double click!");
    }

    /// <summary>
    /// Called when the user drags anything over the diagram.
    /// Return true if the dragged object can be dropped on the current target.
    /// </summary>
    /// <param name="targetMergeElement">The shape or diagram that the mouse is currently over</param>
    /// <param name="diagramDragEventArgs">Data about the dragged element.</param>
    /// <returns></returns>
    public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      // This handler only allows items to be dropped onto the diagram:
      return targetMergeElement is MefDsl2Diagram &&
      // And only accepts files dragged from Windows Explorer:
        diagramDragEventArgs.Data.GetFormats().Contains("FileNameW");
    }

    /// <summary>
    /// Called when the user drops an item onto the diagram.
    /// </summary>
    /// <param name="targetDropElement"></param>
    /// <param name="diagramDragEventArgs"></param>
    public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      MefDsl2Diagram diagram = targetDropElement as MefDsl2Diagram;
      if (diagram == null) return;

      // This handler only accepts files dragged from Windows Explorer:
      string[] draggedFileNames = diagramDragEventArgs.Data.GetData("FileNameW") as string[];
      if (draggedFileNames == null || draggedFileNames.Length == 0) return;

      using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("file names"))
      {
        // Create an element to represent each file:
        foreach (string fileName in draggedFileNames)
        {
          ExampleElement element = new ExampleElement(diagram.ModelElement.Partition);
          element.Name = fileName;

          // This method of adding the new element allows the position
          // of the shape to be specified:
          ElementGroup group = new ElementGroup(element);
          diagram.ElementOperations.MergeElementGroupPrototype(
            diagram, group.CreatePrototype(), PointD.ToPointF(diagramDragEventArgs.MousePosition));
        }
        t.Commit();
      }
    }
  }
}
```

### <a name="validation-constraints"></a>유효성 검사 제약 조건

유효성 검사 메서드는 `ValidationExtension` DSL 및에 의해 생성 된 특성으로 표시 됩니다 <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> . 메서드는 특성으로 표시 되지 않은 모든 클래스에 나타날 수 있습니다.

자세한 내용은 [도메인별 언어의 유효성 검사](../modeling/validation-in-a-domain-specific-language.md)를 참조 하세요.

```csharp
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.Validation;

namespace MefExtension
{
  class MyValidationExtension // Can be any class.
  {
    // SAMPLE VALIDATION METHOD.
    // All validation methods have the following attributes.

    // Specific to the extended DSL:
    [MyDslValidationExtension]

    // Determines when validation is applied:
    [ValidationMethod(
       ValidationCategories.Save
     | ValidationCategories.Open
     | ValidationCategories.Menu)]

    /// <summary>
    /// When validation is executed, this method is invoked
    /// for every element in the model that is an instance
    /// of the second parameter type.
    /// </summary>
    /// <param name="context">For reporting errors</param>
    /// <param name="elementToValidate"></param>
    private void ValidateClassNames
      (ValidationContext context,
       // Type determines to what elements this will be applied:
       ExampleElement elementToValidate)
    {
      // Write code here to test values and links.
      if (elementToValidate.Name.IndexOf(' ') >= 0)
      {
        // Log any unacceptable values:
        context.LogError(
          // Description:
          "Name must not contain spaces"
          // Error code unique to this type of error:
          , "MyDsl001"
          // Element to highlight when user double-clicks error:
          , elementToValidate);
} } } }
```

## <a name="see-also"></a>참조

- [Visual Studio 확장 전달](../extensibility/shipping-visual-studio-extensions.md)
- [MEF(Managed Extensibility Framework)](/dotnet/framework/mef/index)
- [방법: 끌어서 놓기 처리기 추가](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [도메인별 언어에서 유효성 검사](../modeling/validation-in-a-domain-specific-language.md)

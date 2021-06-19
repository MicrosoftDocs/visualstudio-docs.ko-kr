---
title: '방법: 도메인별 언어 디자이너 확장'
description: DSL(도메인 특정 언어) 정의를 편집하는 데 사용하는 디자이너를 확장할 수 있는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9354e3b846f48a79aa5cdd0f39a159bd007cdd3
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387219"
---
# <a name="how-to-extend-the-domain-specific-language-designer"></a>방법: 도메인별 언어 디자이너 확장

DSL 정의를 편집하는 데 사용하는 디자이너를 확장할 수 있습니다. 만들 수 있는 확장 유형에는 메뉴 명령 추가, 끌기 및 두 번 클릭 제스처에 대한 처리기 추가, 특정 형식의 값 또는 관계가 변경될 때 트리거되는 규칙이 포함됩니다. 확장은 VSIX(Visual Studio Integration Extension)로 패키지하고 다른 사용자에게 배포할 수 있습니다.

샘플 코드 및 이 기능에 대한 자세한 내용은 Visual Studio [시각화 및 모델링 SDK를 참조하세요.](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

## <a name="set-up-the-solution"></a>솔루션 설정

확장 코드가 포함된 프로젝트와 프로젝트를 내보내는 VSIX 프로젝트를 설정합니다. 솔루션에는 동일한 VSIX에 통합된 다른 프로젝트가 포함될 수 있습니다.

### <a name="to-create-a-dsl-designer-extension-solution"></a>DSL 디자이너 확장 솔루션을 만들려면

1. 클래스 라이브러리 프로젝트 템플릿을 사용하여 새 프로젝트를 **만듭니다.** 이 프로젝트에는 확장 코드가 포함됩니다.

2. 새 **VSIX 프로젝트** 프로젝트를 만듭니다.

     **솔루션에 추가를** 선택합니다.

     *Source.extension.vsixmanifest가* VSIX 매니페스트 편집기에서 열립니다.

3. 콘텐츠 필드 위에서 **콘텐츠 추가를** 클릭합니다.

4. 콘텐츠 **추가** 대화 상자에서 **콘텐츠 형식 선택을** **MEF 구성 요소** 로 설정하고 **프로젝트를** 클래스 라이브러리 프로젝트로 설정합니다.

5. 버전 선택을 클릭하고 **Visual Studio Enterprise** 선택되어 있는지 **확인합니다.**

6. VSIX 프로젝트가 솔루션의 시작 프로젝트인지 확인합니다.

7. 클래스 라이브러리 프로젝트에서 다음 어셈블리에 대한 참조를 추가합니다.

     Microsoft.VisualStudio.CoreUtility

     Microsoft.VisualStudio.Modeling.Sdk.11.0

     Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

     Microsoft.VisualStudio.Modeling.Sdk.DslDefinition.11.0

     Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0

     System.ComponentModel.Composition

     System.Drawing

     System.Drawing.Design

     System.Windows.Forms

## <a name="test-and-deployment"></a>테스트 및 배포

이 항목의 확장을 테스트하려면 솔루션을 빌드하고 실행합니다. Visual Studio의 실험적 인스턴스가 열립니다. 이 인스턴스에서 DSL 솔루션을 엽니다. DslDefinition 다이어그램을 편집합니다. 확장 동작을 볼 수 있습니다.

주 Visual Studio 및 다른 컴퓨터에 확장을 배포하려면 다음 단계를 수행합니다.

1. VSIX 프로젝트의 bin \\ * \\ \* .vsix에서 VSIX 설치 파일을 찾습니다.

2. 이 파일을 대상 컴퓨터에 복사한 다음 Windows 탐색기(또는 파일 탐색기) 두 번 클릭합니다.

     Visual Studio 확장 관리자가 열리고 확장이 설치되었는지 확인합니다.

확장을 제거하려면 다음 단계를 수행합니다.

1. Visual Studio **도구** 메뉴에서 **확장 관리자** 를 클릭합니다.

2. 확장을 선택하고 삭제합니다.

## <a name="add-a-shortcut-menu-command"></a>바로 가기 메뉴 명령 추가

바로 가기 메뉴 명령이 DSL 디자이너 또는 DSL 탐색기 창에 표시되도록 하려면 다음과 유사한 클래스를 작성합니다.

클래스는 를 구현해야 `ICommandExtension` 하며 특성이 있어야 `DslDefinitionModelCommandExtension` 합니다.

```csharp
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.DslDefinition;
using Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.DslDesigner;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace Fabrikam.SimpleDslDesignerExtension
{
  /// <summary>
  /// Command extending the DslDesigner.
  /// </summary>
  [DslDefinitionModelCommandExtension]
  public class MyDslDesignerCommand : ICommandExtension
  {
    /// <summary>
    /// Selection Context for this command
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Is the command visible and active?
    /// This is called when the user right-clicks.
    /// </summary>
    public void QueryStatus(IMenuCommand command)
    {
      command.Visible = true;
      // Is there any selected DomainClasses in the Dsl explorer?
      command.Enabled =
        SelectionContext.AtLeastOneSelected<DomainClass>();

      // Is there any selected ClassShape on the design surface?
      command.Enabled |=
        (SelectionContext.GetCurrentSelection<ClassShape>()
                .Count() > 0);
    }
    /// <summary>
    /// Executes the command
    /// </summary>
    /// <param name="command">Command initiating this action</param>
    public void Execute(IMenuCommand command)
    {
      ...
    }
    /// <summary>
    /// Label for the command
    /// </summary>
    public string Text
    {
      get { return "My Command"; }
    }
  }
}
```

## <a name="handle-mouse-gestures"></a>마우스 제스처 처리

코드는 메뉴 명령의 코드와 비슷합니다.

```csharp
[DslDefinitionModelGestureExtension]
 class MouseGesturesExtensions : IGestureExtension
 {
  /// <summary>
  /// Double-clicking on a shape representing a Domain model element displays this model element in a dialog box
  /// </summary>
  /// <param name="targetElement">Shape element on which the user has clicked</param>
  /// <param name="diagramPointEventArgs">event args for this double-click</param>
  public void OnDoubleClick(ShapeElement targetElement,
       DiagramPointEventArgs diagramPointEventArgs)
  {
   ModelElement modelElement = PresentationElementHelper.
        GetDslDefinitionModelElement(targetElement);
   if (modelElement != null)
   {
    MessageBox.Show(string.Format(
      "Double clicked on {0}", modelElement.ToString()),
      "Model element double-clicked");
   }
  }

  /// <summary>
  /// Tells if the DslDesigner can consume the to-be-dropped information
  /// </summary>
  /// <param name="targetMergeElement">Shape on which we try to drop</param>
  /// <param name="diagramDragEventArgs">Drop event</param>
  /// <returns><c>true</c> if we can consume the to be dropped data, and <c>false</c> otherwise</returns>
  public bool CanDragDrop(ShapeElement targetMergeElement,
        DiagramDragEventArgs diagramDragEventArgs)
  {
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))
   {
    diagramDragEventArgs.Effect = DragDropEffects.Copy;
    return true;
   }
   return false;
  }

  /// <summary>
  /// Processes the drop by displaying the dropped text
  /// </summary>
  /// <param name="targetMergeElement">Shape on which we dropped</param>
  /// <param name="diagramDragEventArgs">Drop event</param>
  public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
  {
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))
   {
    string[] droppedFiles =
      diagramDragEventArgs.Data.
               GetData(DataFormats.FileDrop) as string[];
    MessageBox.Show(string.Format("Dropped text {0}",
        string.Join("\r\n", droppedFiles)), "Dropped Text");
   }
  }
 }
```

## <a name="respond-to-value-changes"></a>값 변경에 응답

이 처리기가 제대로 작동하려면 도메인 모델이 필요합니다. 간단한 도메인 모델을 제공합니다.

```csharp
using System.Diagnostics;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.DslDefinition;
namespace Fabrikam.SimpleDslDesignerExtension
{
  /// <summary>
  /// Rule firing when the type of a domain model property is changed. The change is displayed
  /// in the debugger (Output window of the Visual Studio instance debugging this extension)
  /// </summary>
  [RuleOn(typeof(PropertyHasType))]
  public class DomainPropertyTypeChangedRule : RolePlayerChangeRule
  {
    /// <summary>
    /// Method called when the Type of a Domain Property
    /// is changed by the user in a DslDefinition
    /// </summary>
    /// <param name="e"></param>
    public override void RolePlayerChanged(RolePlayerChangedEventArgs e)
    {
      // We are only interested in the type
      if (e.DomainRole.Id == PropertyHasType.TypeDomainRoleId)
      {
        PropertyHasType relationship =
           e.ElementLink as PropertyHasType;
        DomainType newType = e.NewRolePlayer as DomainType;
        DomainType oldType = e.OldRolePlayer as DomainType;
        DomainProperty property = relationship.Property;

         // We write about the Type change in the debugguer
        Debug.WriteLine(string.Format("The type of the Domain property '{0}' of domain class '{1}' changed from '{2}' to '{3}'",
          property.Name,
          property.Class.Name,
          oldType.GetFullName(false),
          newType.GetFullName(false))
} }  }  );
```

다음 코드는 간단한 모델을 구현합니다. 자리 표시자를 바꿀 새 GUID를 만듭니다.

```csharp
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.DslDefinition;
namespace Fabrikam.SimpleDslDesignerExtension
{
    /// <summary>
    /// Simplest possible domain model
    /// needed only for extension rules.
    /// </summary>
    [DomainObjectId(SimpleDomainModelExtension.DomainModelId)]
    public class SimpleDomainModelExtension : DomainModel
    {
        // Id of this domain model extension
        // Please replace this with a new GUID:
        public const string DomainModelId =
                  "00000000-0000-0000-0000-000000000000";

        /// <summary>
        /// Constructor for the domain model extension
        /// </summary>
        /// <param name="store">Store in which the domain model will be loaded</param>
        public SimpleDomainModelExtension(Store store)
            : base(store, new Guid(SimpleDomainModelExtension.DomainModelId))
        {

        }

        /// <summary>
        /// Rules brought by this domain model extension
        /// </summary>
        /// <returns></returns>
        protected override System.Type[] GetCustomDomainModelTypes()
        {
            return new Type[] {
                     typeof(DomainPropertyTypeChangedRule)
                              };
        }
    }

    /// <summary>
    /// Provider for the DomainModelExtension
    /// </summary>
    [Export(typeof(DomainModelExtensionProvider))]    [ProvidesExtensionToDomainModel(typeof(DslDefinitionModelDomainModel))]
    public class SimpleDomainModelExtensionProvider
          : DomainModelExtensionProvider
    {
        /// <summary>
        /// Extension model type
        /// </summary>
        public override Type DomainModelType
        {
            get
            {
                return typeof(SimpleDomainModelExtension);
            }
        }

    }
}
```
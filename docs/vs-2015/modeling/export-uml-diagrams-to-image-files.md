---
title: UML 다이어그램을 이미지 파일로 내보내기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: b29ce2a5-0ee3-4ab7-9aa3-13ca9c6b37a2
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c095291cd02d591d9e493601b598a63c1ccb6f5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669663"
---
# <a name="export-uml-diagrams-to-image-files"></a>UML 다이어그램을 이미지 파일로 내보내기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로그램 제어 아래에 있는 이미지로 UML 문서를 내보낼 수 있습니다. 예를 들어 자동 문서 생성의 일부로 이 작업을 수행할 수 있습니다.

 수동으로 문서를 이미지로 내보내려는 경우 다이어그램에서 모양을 복사하고 Word 등의 다른 프로그램에 붙여넣을 수 있습니다. 문서를 XPS 형식으로 인쇄할 수도 있습니다. 자세한 내용은 [다이어그램을 이미지로 내보내기](../modeling/export-diagrams-as-images.md)를 참조 하세요.

## <a name="saving-an-image"></a>이미지 저장
 다음 코드에서는 이미지를 파일에 저장하는 바로 가기 메뉴 명령(상황에 맞는 메뉴 명령이라고도 함)을 정의합니다.

> [!NOTE]
> 이 코드를 메뉴 명령으로 실행하려면 MEF 구성 요소에 통합해야 합니다. 자세한 내용은 [모델링 다이어그램에서 메뉴 명령 정의](../modeling/define-a-menu-command-on-a-modeling-diagram.md)를 참조 하세요.

 이 코드는 먼저 [Ishape. GetObject](/previous-versions/ee789371(v=vs.140)) 를 사용 하 여 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> 기본 구현의을 가져옵니다. 이 형식에는 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.CreateBitmap%2A> 메서드가 있습니다.

```
namespace SaveToImage
{
  using System.ComponentModel.Composition; // for [Import], [Export]
  using System.Drawing; // for Bitmap
  using System.Drawing.Imaging; // for ImageFormat
  using System.Linq; // for collection extensions
  using System.Windows.Forms; // for SaveFileDialog
  using Microsoft.VisualStudio.Modeling.Diagrams;
    // for Diagram
  using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
    // for IGestureExtension, ICommandExtension, ILinkedUndoContext
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
    // for IDiagramContext
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
    // for designer extension attributes

  /// <summary>
  /// Called when the user clicks the menu item.
  /// </summary>
  // Context menu command applicable to any UML diagram
  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  [UseCaseDesignerExtension]
  [SequenceDesignerExtension]
  [ComponentDesignerExtension]
  [ActivityDesignerExtension]
  class CommandExtension : ICommandExtension
  {
    [Import]
    IDiagramContext Context { get; set; }

    public void Execute(IMenuCommand command)
    {
      // Get the diagram of the underlying implementation.
      Diagram dslDiagram = Context.CurrentDiagram.GetObject<Diagram>();
      if (dslDiagram != null)
      {
        string imageFileName = FileNameFromUser();
        if (!string.IsNullOrEmpty(imageFileName))
        {
          Bitmap bitmap = dslDiagram.CreateBitmap(
           dslDiagram.NestedChildShapes,
           Diagram.CreateBitmapPreference.FavorClarityOverSmallSize);
          bitmap.Save(imageFileName, GetImageType(imageFileName));
        }
      }
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Set Enabled and Visible to specify the menu item status.
    /// </summary>
    /// <param name="command"></param>
    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled = Context.CurrentDiagram != null
        && Context.CurrentDiagram.ChildShapes.Count() > 0;
    }

    /// <summary>
    /// Menu text.
    /// </summary>
    public string Text
    {
      get { return "Save To Image..."; }
    }

    /// <summary>
    /// Ask the user for the path of an image file.
    /// </summary>
    /// <returns>image file path, or null</returns>
    private string FileNameFromUser()
    {
      SaveFileDialog dialog = new SaveFileDialog();
      dialog.AddExtension = true;
      dialog.DefaultExt = "image.bmp";
      dialog.Filter = "Bitmap ( *.bmp )|*.bmp|JPEG File ( *.jpg )|*.jpg|Enhanced Metafile (*.emf )|*.emf|Portable Network Graphic ( *.png )|*.png";
      dialog.FilterIndex = 1;
      dialog.Title = "Save Diagram to Image";
      return dialog.ShowDialog() == DialogResult.OK ? dialog.FileName : null;
    }

    /// <summary>
    /// Return the appropriate image type for a file extension.
    /// </summary>
    /// <param name="fileName"></param>
    /// <returns></returns>
    private ImageFormat GetImageType(string fileName)
    {
      string extension = System.IO.Path.GetExtension(fileName).ToLowerInvariant();
      ImageFormat result = ImageFormat.Bmp;
      switch (extension)
      {
        case ".jpg":
          result = ImageFormat.Jpeg;
          break;
        case ".emf":
          result = ImageFormat.Emf;
          break;
        case ".png":
          result = ImageFormat.Png;
          break;
      }
      return result;
    }
  }
}
```

## <a name="see-also"></a>관련 항목
 [다이어그램을 이미지로 내보내기](../modeling/export-diagrams-as-images.md) [모델링 다이어그램의 메뉴 명령 정의](../modeling/define-a-menu-command-on-a-modeling-diagram.md)

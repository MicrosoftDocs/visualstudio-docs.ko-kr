---
title: '방법: 인쇄할 때 워크시트에서 컨트롤 숨기기'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 336723f60a2cd90dc63db24e981dd06e0388cb9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544809"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>방법: 인쇄할 때 워크시트에서 컨트롤 숨기기
  Windows Forms 컨트롤을 포함 하는 Microsoft Office Excel 문서를 인쇄 하면 컨트롤이 인쇄 된 워크시트에 표시 됩니다. 워크시트를 인쇄할 때 컨트롤을 숨길 수 있습니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> 와 같은 데이터를 표시 하는 컨트롤을 숨기면 <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> 컨트롤의 데이터가 인쇄 된 워크시트에 표시 되지 않습니다.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>워크시트가 인쇄 될 때 컨트롤을 숨기려면

1. Visual Studio에서 Excel 프로젝트를 만들거나 열고 **Sheet1** 이 디자이너에 표시 되는지 확인 합니다. 프로젝트 만들기에 대 한 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

2. **도구 상자**의 **공용 컨트롤** 탭에서 <xref:Microsoft.Office.Tools.Excel.Controls.Button> 컨트롤을의 셀로 끌어 옵니다 `Sheet1` .

3. **속성** 창에서 <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> 속성을 **False**로 설정 합니다.

## <a name="see-also"></a>참조
- [Office 문서의 컨트롤](../vsto/controls-on-office-documents.md)
- [Office 문서에 대 한 Windows Forms 컨트롤 개요](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [방법: Office 문서에 Windows Forms 컨트롤 추가](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [방법: 워크시트 셀에서 컨트롤 크기 조정](../vsto/how-to-resize-controls-within-worksheet-cells.md)

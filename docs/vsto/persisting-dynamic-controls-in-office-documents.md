---
title: Office 문서에서 동적 컨트롤 유지
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Office documents [Office development in Visual Studio, host controls
- controls [Office development in Visual Studio], persisting in the document
- Windows Forms controls [Office development in Visual Studio], persisting in the document
- documents [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], persisting in the document
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5d48dfab18ec2165753ac19330f7fbe18c923da9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255998"
---
# <a name="persist-dynamic-controls-in-office-documents"></a>Office 문서에서 동적 컨트롤 유지

문서 또는 통합 문서를 저장하고 닫으면 런타임에 추가한 컨트롤이 유지되지 않습니다. 정확한 동작은 호스트 컨트롤 및 Windows Forms 컨트롤에서 서로 다릅니다. 두 경우 모두, 사용자가 문서를 다시 열 때 컨트롤을 다시 만드는 코드를 솔루션에 추가할 수 있습니다.

런타임에 문서에 추가하는 컨트롤을 *동적 컨트롤*이라고 합니다. 동적 컨트롤에 대 한 자세한 내용은 [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)를 참조 하세요.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="persist-host-controls-in-the-document"></a>문서에 호스트 컨트롤 유지

문서를 저장하고 닫으면 모든 동적 호스트 컨트롤이 문서에서 제거됩니다. 기본 네이티브 Office 개체만 남아 있습니다. 예를 들어 <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> 호스트 컨트롤은 <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName>가 됩니다. 네이티브 Office 개체는 호스트 컨트롤 이벤트에 연결되어 있지 않으며 호스트 컨트롤의 데이터 바인딩 기능이 없습니다.

다음 표에서는 각 호스트 컨트롤 유형에 대해 문서에 남아 있는 네이티브 Office 개체를 보여 줍니다.

|호스트 컨트롤 형식|네이티브 Office 개체 형식|
|-----------------------|-------------------------------|
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|

### <a name="re-create-dynamic-host-controls-when-documents-are-opened"></a>문서를 열 때 동적 호스트 컨트롤 다시 만들기

사용자가 문서를 열 때마다 기존 네이티브 컨트롤 대신 동적 호스트 컨트롤을 다시 만들 수 있습니다. 문서를 열 때 이런 방식으로 호스트 컨트롤을 만들면 사용자가 예상하는 환경이 시뮬레이트됩니다.

Word 용 호스트 컨트롤 또는 <xref:Microsoft.Office.Tools.Excel.NamedRange> Excel 용 또는 호스트 컨트롤을 다시 만들려면 <xref:Microsoft.Office.Tools.Excel.ListObject> `Add` \<*control class*> 또는 개체의 메서드를 사용 <xref:Microsoft.Office.Tools.Excel.ControlCollection?displayProperty=fullName> <xref:Microsoft.Office.Tools.Word.ControlCollection?displayProperty=fullName> 합니다. 네이티브 Office 개체에 대한 매개 변수가 있는 메서드를 사용합니다.

예를 들어 문서를 열 때 기존 네이티브 <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> 에서 <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName> 호스트 컨트롤을 만들려는 경우 <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> 메서드를 사용하고 기존 <xref:Microsoft.Office.Interop.Excel.ListObject>를 전달합니다. 다음 코드 예제에서는 Excel용 문서 수준 프로젝트에서 이 과정을 보여 줍니다. 코드는 <xref:Microsoft.Office.Tools.Excel.ListObject> 클래스의 <xref:Microsoft.Office.Interop.Excel.ListObject> 라는 기존 `MyListObject` 를 기반으로 하는 동적 `Sheet1` 를 다시 만듭니다.

[!code-csharp[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/Sheet1.cs#6)]
[!code-vb[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/Sheet1.vb#6)]

### <a name="re-create-chart"></a>차트 다시 만들기

호스트 컨트롤을 다시 만들려면 <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> 먼저 네이티브를 삭제 한 <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName> 다음 <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> 메서드를 사용 하 여를 다시 만들어야 합니다 <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> . `Add` \<*control class*> 기존을 기반으로 새을 만들 수 있는 메서드는 없습니다 <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName> .

네이티브를 먼저 삭제 하지 않으면를 <xref:Microsoft.Office.Interop.Excel.Chart> 다시 만들 때 두 번째 중복 차트를 만듭니다 <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> .

## <a name="persist-windows-forms-controls-in-documents"></a>문서의 Windows Forms 컨트롤 유지

문서를 저장하고 닫으면 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 이 동적으로 생성된 모든 Windows Forms 컨트롤을 문서에서 자동으로 제거합니다. 그러나 이 동작은 문서 수준 및 VSTO 추가 기능 프로젝트에서 서로 다릅니다.

문서 수준 사용자 지정에서는 다음에 문서를 열 때 컨트롤 및 기본 ActiveX 래퍼(문서의 컨트롤을 호스트하는 데 사용)가 제거됩니다. 컨트롤이 있었다는 표시가 없습니다.

VSTO 추가 기능에서는 컨트롤이 제거되지만 ActiveX 래퍼가 문서에 남아 있습니다. 다음에 사용자가 문서를 열면 ActiveX 래퍼가 표시됩니다. Excel에서 ActiveX 래퍼는 마지막으로 문서를 저장할 때 표시된 대로 컨트롤의 이미지를 표시합니다. Word에서 ActiveX 래퍼는 사용자가 클릭하지 않을 경우 표시되지 않으며, 클릭하면 컨트롤의 테두리를 나타내는 점선이 표시됩니다. 여러 가지 방법으로 ActiveX 래퍼를 제거할 수 있습니다. 자세한 내용은 [추가 기능에서 ActiveX 래퍼 제거](#removingActiveX)를 참조 하세요.

### <a name="re-create-windows-forms-controls-when-documents-are-opened"></a>문서를 열 때 Windows Forms 컨트롤 다시 만들기

사용자는 문서를 다시 열 때 삭제된 Windows Forms 컨트롤을 다시 만들 수 있습니다. 이렇게 하려면 솔루션이 다음 작업을 수행해야 합니다.

1. 문서를 저장하거나 닫을 때 컨트롤의 크기, 위치 및 상태에 대한 정보를 저장합니다. 문서 수준 사용자 지정에서 문서의 데이터 캐시에 데이터를 저장할 수 있습니다. VSTO 추가 기능에서 문서의 사용자 지정 XML 부분에 데이터를 저장할 수 있습니다.

2. 문서를 열 때 발생하는 이벤트에서 컨트롤을 다시 만듭니다. 문서 수준 프로젝트에서는 `Sheet` *n* `_Startup` 또는 이벤트 처리기에서이 작업을 수행할 수 있습니다 `ThisDocument_Startup` . VSTO 추가 기능 프로젝트에서는 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> 또는 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> 이벤트에 대한 이벤트 처리기에서 이 작업을 수행할 수 있습니다.

### <a name="remove-activex-wrappers-in-an-add-in"></a><a name="removingActiveX"></a> 추가 기능에서 ActiveX 래퍼 제거

VSTO 추가 기능을 사용 하 여 문서에 동적 Windows Forms 컨트롤을 추가 하는 경우 다음과 같은 방법으로 다음에 열 때 컨트롤에 대 한 ActiveX 래퍼가 문서에 표시 되지 않도록 방지할 수 있습니다.

#### <a name="remove-activex-wrappers-when-the-document-is-opened"></a>문서를 열 때 ActiveX 래퍼 제거

모든 ActiveX 래퍼를 제거하려면 `GetVstoObject` 메서드를 호출하여 새로 열린 문서를 나타내는 <xref:Microsoft.Office.Interop.Word.Document> 또는 <xref:Microsoft.Office.Interop.Excel.Workbook>에 대한 호스트 항목을 생성합니다. 예를 들어 Word 문서에서 모든 ActiveX 래퍼를 제거하려면 `GetVstoObject` 메서드를 호출하여 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> 이벤트의 이벤트 처리기에 전달되는 <xref:Microsoft.Office.Interop.Word.Document> 개체에 대한 호스트 항목을 생성할 수 있습니다.

이 절차는 VSTO 추가 기능이 설치되어 있는 컴퓨터에서만 문서가 열리는 것을 알고 있는 경우에 유용합니다. VSTO 추가 기능이 설치되어 있지 않은 다른 사용자에게 문서가 전달될 수 있는 경우 문서를 닫기 전에 컨트롤을 제거하는 것이 좋습니다.

다음 코드 예제에서는 문서를 열 때 `GetVstoObject` 메서드를 호출하는 방법을 보여 줍니다.

[!code-vb[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#11)]
[!code-csharp[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#11)]

메서드는 `GetVstoObject` 런타임에 새 호스트 항목을 생성 하는 데 주로 사용 되지만,이 메서드는 특정 문서에 대해 처음 호출 될 때 문서에서 모든 ActiveX 래퍼를 지웁니다. 메서드를 사용 하는 방법에 대 한 자세한 내용은 `GetVstoObject` [런타임에 VSTO 추가 기능에서 Word 문서 및 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)을 참조 하세요.

문서를 열 때 VSTO 추가 기능에서 동적 컨트롤을 만드는 경우 VSTO 추가 기능에서는 이미 `GetVstoObject` 컨트롤을 만드는 프로세스의 일부로 메서드를 호출 합니다. 이 시나리오에서는 ActiveX 래퍼를 제거하기 위해 `GetVstoObject` 메서드에 대한 별도 호출을 추가할 필요가 없습니다.

#### <a name="remove-the-dynamic-controls-before-the-document-is-closed"></a>문서를 닫기 전에 동적 컨트롤 제거

문서를 닫기 전에 VSTO 추가 기능이 문서에서 각 동적 컨트롤을 명시적으로 제거할 수 있습니다. 이 절차는 VSTO 추가 기능이 설치되어 있지 않은 다른 사용자에게 전달될 수 있는 문서에 유용합니다.

다음 코드 예제에서는 문서를 닫을 때 Word 문서에서 모든 Windows Forms 컨트롤을 제거하는 방법을 보여 줍니다.

[!code-vb[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#10)]
[!code-csharp[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#10)]

## <a name="see-also"></a>참조

- [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)

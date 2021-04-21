---
title: '방법: 프로그래밍 방식으로 통합 문서 저장'
description: 메모리에 열려 있는 통합 문서를 수정 하지 않고 경로를 변경 하 고 통합 문서 복사본을 저장 하지 않고 프로그래밍 방식으로 Microsoft Excel 통합 문서를 저장 합니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, saving in XML format
- workbooks, saving
- workbooks, saving backup copies
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4559d098a80a1dfd8f1d3f5c2c21cbebc992fcb7
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828984"
---
# <a name="how-to-programmatically-save-workbooks"></a>방법: 프로그래밍 방식으로 통합 문서 저장
  통합 문서를 저장하는 방법에는 여러 가지가 있습니다. 경로를 변경하지 않고 통합 문서를 저장할 수 있습니다. 통합 문서가 이전에 저장되지 않은 경우 경로를 지정하여 통합 문서를 저장해야 합니다. 명시적 경로 없이 Microsoft Office Excel은 파일을 만들 때 지정된 이름으로 현재 폴더에 파일을 저장합니다. 메모리에 열려 있는 통합 문서를 수정하지 않고 통합 문서의 복사본을 저장할 수도 있습니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="save-a-workbook-without-changing-the-path"></a>경로를 변경 하지 않고 통합 문서 저장

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>문서 수준 사용자 지정과 연결된 통합 문서를 저장하려면

1. <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> 클래스의 `ThisWorkbook` 메서드를 호출합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet4":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>VSTO 추가 기능에서 활성 통합 문서를 저장하려면

1. <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> 메서드를 호출하여 활성 통합 문서를 저장합니다. 다음 코드 예제를 사용하려면 Excel용 VSTO 추가 기능 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet3":::

## <a name="save-a-workbook-with-a-new-path"></a>새 경로를 사용 하 여 통합 문서 저장
 필요에 따라 파일 형식, 암호, 액세스 모드 등을 지정하여 지정된 통합 문서를 새 위치나 새 이름으로 저장할 수 있습니다.

> [!NOTE]
> <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A>일부 형식으로 저장 하려면 상호 작용이 필요 하므로 새 경로를 사용 하 여 통합 문서를 저장 하기 전에 속성을 **False** 로 설정 하는 것이 좋습니다. 이 속성을 **False** 로 설정 하면 Excel에서 모든 기본값을 사용 합니다.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>문서 수준 사용자 지정과 연결된 통합 문서를 저장하려면

1. <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> 클래스의 `ThisWorkbook` 메서드를 호출합니다. 다음 코드 예제를 사용하려면 `ThisWorkbook` 클래스에서 실행합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet5":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>VSTO 추가 기능에서 활성 통합 문서를 저장하려면

1. <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> 메서드를 호출하여 활성 통합 문서를 새 경로에 저장합니다. 다음 코드 예제를 사용하려면 Excel용 VSTO 추가 기능 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet4":::

## <a name="save-a-copy-of-the-workbook"></a>통합 문서의 복사본 저장
 메모리에 열려 있는 통합 문서를 수정하지 않고 통합 문서의 복사본을 파일에 저장할 수 있습니다. 이 기능은 통합 문서의 위치를 수정하지 않고 백업 복사본을 만들려는 경우에 유용합니다.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>문서 수준 사용자 지정과 연결된 통합 문서를 저장하려면

1. <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> 클래스의 `ThisWorkbook` 메서드를 호출합니다. 다음 코드 예제를 사용하려면 `ThisWorkbook` 클래스에서 실행합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet6":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>VSTO 추가 기능에서 활성 통합 문서를 저장하려면

1. <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> 메서드를 호출하여 활성 통합 문서의 복사본을 저장합니다. 다음 코드 예제를 사용하려면 Excel용 VSTO 추가 기능 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet5":::

## <a name="robust-programming"></a>강력한 프로그래밍
 통합 문서를 저장하거나 복사하는 메서드를 대화형으로 취소하면 코드에서 런타임 오류가 발생합니다. 예를 들어 프로시저에서 메서드를 호출 <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> 하지만 excel에서 프롬프트를 사용 하지 않는 경우 사용자가 메시지가 표시 되 면 **취소** 를 클릭 하면 excel에서 런타임 오류가 발생 합니다.

## <a name="see-also"></a>참조
- [통합 문서 작업](../vsto/working-with-workbooks.md)
- [통합 문서 호스트 항목](../vsto/workbook-host-item.md)
- [방법: 프로그래밍 방식으로 통합 문서 닫기](../vsto/how-to-programmatically-close-workbooks.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍에 대 한 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)

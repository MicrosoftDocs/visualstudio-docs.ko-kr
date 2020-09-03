---
title: '방법: 프로그래밍 방식으로 Word 표 만들기'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding tables
- tables [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a1bc20b277df90ae963d257137373457a0196e72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544757"
---
# <a name="how-to-programmatically-create-word-tables"></a>방법: 프로그래밍 방식으로 Word 표 만들기
  <xref:Microsoft.Office.Interop.Word.Tables> 컬렉션은 <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection> 및 <xref:Microsoft.Office.Interop.Word.Range> 클래스의 멤버이므로 이러한 컨텍스트 중 하나에서 표를 만들 수 있습니다. <xref:Microsoft.Office.Interop.Word.Tables> 컬렉션의 <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> 메서드를 사용하여 지정된 범위에 표를 추가합니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="create-tables-in-document-level-customizations"></a>문서 수준 사용자 지정에서 테이블 만들기

### <a name="to-add-a-table-to-a-document"></a>문서에 테이블을 추가 하려면

- <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> 메서드를 사용하여 문서의 시작 부분에 행 3개와 열 4개로 구성된 표를 추가합니다.

   다음 코드 예제를 사용하려면 프로젝트의 `ThisDocument` 클래스에서 실행합니다.

   [!code-vb[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#86)]
   [!code-csharp[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#86)]

  표를 만들면 <xref:Microsoft.Office.Tools.Word.Document> 호스트 항목의 <xref:Microsoft.Office.Interop.Word.Tables> 컬렉션에 자동으로 추가됩니다. 그런 후에 다음 코드와 같이 <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> 속성을 사용하여 해당 항목 번호로 표를 참조할 수 있습니다.

### <a name="to-refer-to-a-table-by-item-number"></a>항목 번호로 표를 참조하려면

1. <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> 속성을 사용하고 참조하려는 표의 항목 번호를 제공합니다.

    다음 코드 예제를 사용하려면 프로젝트의 `ThisDocument` 클래스에서 실행합니다.

    [!code-vb[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#87)]
    [!code-csharp[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#87)]

   각 <xref:Microsoft.Office.Interop.Word.Table> 개체에는 서식 특성을 설정할 수 있게 해주는 <xref:Microsoft.Office.Interop.Word.Table.Range%2A> 속성도 있습니다.

### <a name="to-apply-a-style-to-a-table"></a>표에 스타일을 적용하려면

1. <xref:Microsoft.Office.Interop.Word.Table.Style%2A> 속성을 사용하여 Word 기본 제공 스타일 중 하나를 표에 적용합니다.

     다음 코드 예제를 사용하려면 프로젝트의 `ThisDocument` 클래스에서 실행합니다.

     [!code-vb[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#88)]

## <a name="create-tables-in-vsto-add-ins"></a>VSTO 추가 기능에서 테이블 만들기

### <a name="to-add-a-table-to-a-document"></a>문서에 테이블을 추가 하려면

- <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> 메서드를 사용하여 문서의 시작 부분에 행 3개와 열 4개로 구성된 표를 추가합니다.

   다음 코드 예제에서는 활성 문서에 표를 추가합니다. 이 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

   [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#86)]
   [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#86)]

  표를 만들면 <xref:Microsoft.Office.Interop.Word.Document>의 <xref:Microsoft.Office.Interop.Word.Tables> 컬렉션에 자동으로 추가됩니다. 그런 후에 다음 코드와 같이 <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> 속성을 사용하여 해당 항목 번호로 표를 참조할 수 있습니다.

### <a name="to-refer-to-a-table-by-item-number"></a>항목 번호로 표를 참조하려면

1. <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> 속성을 사용하고 참조하려는 표의 항목 번호를 제공합니다.

    다음 코드 예제에서는 활성 문서를 사용합니다. 이 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#87)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#87)]

   각 <xref:Microsoft.Office.Interop.Word.Table> 개체에는 서식 특성을 설정할 수 있게 해주는 <xref:Microsoft.Office.Interop.Word.Table.Range%2A> 속성도 있습니다.

### <a name="to-apply-a-style-to-a-table"></a>표에 스타일을 적용하려면

1. <xref:Microsoft.Office.Interop.Word.Table.Style%2A> 속성을 사용하여 Word 기본 제공 스타일 중 하나를 표에 적용합니다.

     다음 코드 예제에서는 활성 문서를 사용합니다. 이 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#88)]

## <a name="see-also"></a>참조
- [방법: 프로그래밍 방식으로 Word 표의 셀에 텍스트 및 서식 추가](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [방법: 프로그래밍 방식으로 Word 표에 행 및 열 추가](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [방법: 프로그래밍 방식으로 문서 속성을 사용 하 여 Word 표 채우기](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)

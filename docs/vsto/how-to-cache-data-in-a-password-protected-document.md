---
title: '방법: 암호로 보호 된 문서의 데이터 캐시'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 12b04b985d54161343d26cdd32178b67bd6e6b91
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547240"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>방법: 암호로 보호 된 문서의 데이터 캐시
  암호로 보호 되는 문서나 통합 문서에서 데이터 캐시에 데이터를 추가 하는 경우 캐시 된 데이터에 대 한 변경 내용은 자동으로 저장 되지 않습니다. 프로젝트에서 두 메서드를 재정의 하 여 캐시 된 데이터에 대 한 변경 내용을 저장할 수 있습니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="caching-in-word-documents"></a>Word 문서에서 캐싱

### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>암호로 보호 되는 Word 문서에 데이터를 캐시 하려면

1. 클래스에서 `ThisDocument` 공용 필드 또는 속성을 캐시 하도록 표시 합니다. 자세한 내용은 [데이터 캐시](../vsto/caching-data.md)를 참조 하세요.

2. <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A>클래스의 메서드를 재정의 `ThisDocument` 하 고 문서에서 보호를 제거 합니다.

     문서를 저장 하면에서 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 이 메서드를 호출 하 여 문서의 보호를 해제할 수 있는 기회를 제공 합니다. 이렇게 하면 캐시 된 데이터에 대 한 변경 내용을 저장할 수 있습니다.

3. <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A>클래스의 메서드를 재정의 `ThisDocument` 하 고 문서에 보호를 다시 적용 합니다.

     문서를 저장 한 후에는 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 이 메서드를 호출 하 여 문서에 보호를 다시 적용할 수 있는 기회를 제공 합니다.

### <a name="example"></a>예제
 다음 코드 예제에서는 암호로 보호 되는 Word 문서에 데이터를 캐시 하는 방법을 보여 줍니다. 코드는 메서드에서 보호를 제거 하기 전에 <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> 현재 <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> 값을 저장 하므로 동일한 형식의 보호가 메서드에서 다시 적용 될 수 있습니다 <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> .

 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]

### <a name="compile-the-code"></a>코드 컴파일
 프로젝트의 클래스에이 코드를 추가 `ThisDocument` 합니다. 이 코드에서는 암호가 이라는 필드에 저장 되어 있다고 가정 `securelyStoredPassword` 합니다.

## <a name="cache-in-excel-workbooks"></a>Excel 통합 문서의 캐시
 Excel 프로젝트에서이 절차는 메서드를 사용 하 여 전체 통합 문서를 암호로 보호 하는 경우에만 필요 <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> 합니다. 메서드를 사용 하 여 특정 워크시트만 암호로 보호 하는 경우에는이 절차가 필요 하지 않습니다 <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> .

### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>암호로 보호 되는 Excel 통합 문서에서 데이터를 캐시 하려면

1. `ThisWorkbook`클래스 또는 n 클래스 중 하나에서 `Sheet` *n* public 필드 또는 속성을 캐시 하도록 표시 합니다. 자세한 내용은 [데이터 캐시](../vsto/caching-data.md)를 참조 하세요.

2. <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A>클래스의 메서드를 재정의 `ThisWorkbook` 하 고 통합 문서에서 보호를 제거 합니다.

     통합 문서를 저장 하면에서 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 이 메서드를 호출 하 여 통합 문서의 보호를 해제할 수 있는 기회를 제공 합니다. 이렇게 하면 캐시 된 데이터에 대 한 변경 내용을 저장할 수 있습니다.

3. <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A>클래스의 메서드를 재정의 `ThisWorkbook` 하 고 문서에 보호를 다시 적용 합니다.

     통합 문서를 저장 한 후에는 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 이 메서드를 호출 하 여 통합 문서에 대 한 보호를 다시 적용할 수 있는 기회를 제공 합니다.

### <a name="example"></a>예제
 다음 코드 예제에서는 암호로 보호 되는 Excel 통합 문서에서 데이터를 캐시 하는 방법을 보여 줍니다. 코드는 메서드에서 보호를 제거 하기 전에 <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> 현재 <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> 및 <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> 값을 저장 하므로 메서드에서 동일한 형식의 보호를 다시 적용할 수 있습니다 <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> .

 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]

### <a name="compile-the-code"></a>코드 컴파일
 프로젝트의 클래스에이 코드를 추가 `ThisWorkbook` 합니다. 이 코드에서는 암호가 이라는 필드에 저장 되어 있다고 가정 `securelyStoredPassword` 합니다.

## <a name="see-also"></a>참고 항목
- [데이터 캐시](../vsto/caching-data.md)
- [방법: 오프 라인 이나 서버에서 사용할 데이터 캐시](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [방법: Office 문서에서 프로그래밍 방식으로 데이터 소스 캐시](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)

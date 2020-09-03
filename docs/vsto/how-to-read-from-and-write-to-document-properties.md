---
title: '방법: 문서 속성에서 읽기 및 문서 속성에 쓰기'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
- Excel [Office development in Visual Studio], document properties
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: adad9ec70290f426ce7c3c59ad13ff8636a69463
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85541325"
---
# <a name="how-to-read-from-and-write-to-document-properties"></a>방법: 문서 속성에서 읽기 및 문서 속성에 쓰기
  문서와 함께 문서 속성을 저장할 수 있습니다. Office 애플리케이션은 작성자, 제목 및 주제와 같은 다양한 기본 제공 속성을 제공합니다. 이 항목에서는 Microsoft Office Excel 및 Microsoft Office Word에서 문서 속성을 설정하는 방법을 보여 줍니다.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

## <a name="set-document-properties-in-excel"></a>Excel에서 문서 속성 설정
 Excel에서 기본 제공 속성으로 작업하려면 다음 속성을 사용합니다.

- 문서 수준 프로젝트에서는 <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> 클래스의 `ThisWorkbook` 속성을 사용합니다.

- VSTO 추가 기능 프로젝트에서는 <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> 개체의 <xref:Microsoft.Office.Interop.Excel.Workbook> 속성을 사용합니다.

  이러한 속성은 <xref:Microsoft.Office.Core.DocumentProperties> 개체 컬렉션인 <xref:Microsoft.Office.Core.DocumentProperty> 개체를 반환합니다. 컬렉션의 `Item` 속성을 사용하여 이름 또는 컬렉션 내의 인덱스로 특정 속성을 검색할 수 있습니다.

  다음 코드 예제에서는 문서 수준 프로젝트에서 기본 제공 **Revision Number** 속성을 변경하는 방법을 보여 줍니다.

### <a name="to-change-the-revision-number-property-in-excel"></a>Excel에서 수정 번호 속성을 변경하려면

1. 기본 제공 문서 속성을 변수에 할당합니다.

     [!code-vb[Trin_VstcoreProgramming#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#7)]
     [!code-csharp[Trin_VstcoreProgramming#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#7)]

2. `Revision Number` 속성을 1씩 증가시킵니다.

     [!code-vb[Trin_VstcoreProgramming#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#8)]
     [!code-csharp[Trin_VstcoreProgramming#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#8)]

## <a name="set-document-properties-in-word"></a>Word에서 문서 속성 설정
 Word에서 기본 제공 속성으로 작업하려면 다음 속성을 사용합니다.

- 문서 수준 프로젝트에서는 <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> 클래스의 `ThisDocument` 속성을 사용합니다.

- VSTO 추가 기능 프로젝트에서는 <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> 개체의 <xref:Microsoft.Office.Interop.Word.Document> 속성을 사용합니다.

  이러한 속성은 <xref:Microsoft.Office.Core.DocumentProperties> 개체 컬렉션인 <xref:Microsoft.Office.Core.DocumentProperty> 개체를 반환합니다. 컬렉션의 `Item` 속성을 사용하여 이름 또는 컬렉션 내의 인덱스로 특정 속성을 검색할 수 있습니다.

  다음 코드 예제에서는 문서 수준 프로젝트에서 기본 제공 **Subject** 속성을 변경하는 방법을 보여 줍니다.

### <a name="to-change-the-subject-property"></a>Subject 속성을 변경하려면

1. 기본 제공 문서 속성을 변수에 할당합니다.

     [!code-csharp[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#1)]

2. `Subject` 속성을 "Whitepaper"로 변경합니다.

     [!code-csharp[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#2)]

## <a name="robust-programming"></a>강력한 프로그래밍
 예제에서는 Excel용 문서 수준 프로젝트의 `ThisWorkbook` 클래스 및 Word용 문서 수준 프로젝트의 `ThisDocument` 클래스에서 코드를 작성했다고 가정합니다.

 Word 및 Excel과 해당 개체로 작업 중이지만 Microsoft Office에서 사용 가능한 기본 제공 문서 속성 목록을 제공합니다. 정의되지 않은 속성에 액세스하려고 하면 예외가 발생합니다.

## <a name="see-also"></a>추가 정보
- [VSTO 추가 기능 프로그램](../vsto/programming-vsto-add-ins.md)
- [문서 수준 사용자 지정 프로그램](../vsto/programming-document-level-customizations.md)
- [방법: 사용자 지정 문서 속성 만들기 및 수정](../vsto/how-to-create-and-modify-custom-document-properties.md)

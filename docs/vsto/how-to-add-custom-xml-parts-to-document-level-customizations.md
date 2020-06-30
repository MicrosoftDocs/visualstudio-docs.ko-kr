---
title: '방법: 문서 수준 사용자 지정에 사용자 지정 XML 부분 추가'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document-level customizations [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 92148a6f084a4cc04b4587781e750e4fd0df133f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538335"
---
# <a name="how-to-add-custom-xml-parts-to-document-level-customizations"></a>방법: 문서 수준 사용자 지정에 사용자 지정 XML 부분 추가
  문서 수준 사용자 지정에서 사용자 지정 XML 부분을 만들어 Microsoft Office Excel 통합 문서 또는 Microsoft Office Word 문서에 XML 데이터를 저장할 수 있습니다. 자세한 내용은 [사용자 지정 XML 부분 개요](../vsto/custom-xml-parts-overview.md)를 참조 하세요.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Visual Studio는 Microsoft Office PowerPoint에 대해 문서 수준 프로젝트를 제공하지 않습니다. VSTO 추가 기능을 사용 하 여 PowerPoint 프레젠테이션에 사용자 지정 XML 부분을 추가 하는 방법에 대 한 자세한 내용은 [방법: Vsto 추가 기능을 사용 하 여 문서에 사용자 지정 xml 부분 추가](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)를 참조 하세요.

### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Excel 통합 문서에 사용자 지정 XML 부분을 추가하려면

1. 통합 문서의 <xref:Microsoft.Office.Core.CustomXMLPart> 컬렉션에 새 <xref:Microsoft.Office.Core.CustomXMLParts> 개체를 추가합니다. <xref:Microsoft.Office.Core.CustomXMLPart> 에는 통합 문서에 저장하려는 XML 문자열이 들어 있습니다.

     [!code-csharp[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.vb#1)]

2. Excel용 문서 수준 프로젝트의 `AddCustomXmlPartToWorkbook` 클래스에 `ThisWorkbook` 메서드를 추가합니다.

3. 프로젝트의 다른 코드에서 메서드를 호출합니다. 예를 들어 사용자가 통합 문서를 열 때 사용자 지정 XML 부분을 만들려면 `ThisWorkbook_Startup` 이벤트 처리기에서 메서드를 호출합니다.

### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Word 문서에 사용자 지정 XML 부분을 추가하려면

1. 문서의 <xref:Microsoft.Office.Core.CustomXMLPart> 컬렉션에 새 <xref:Microsoft.Office.Core.CustomXMLParts> 개체를 추가합니다. <xref:Microsoft.Office.Core.CustomXMLPart> 에는 문서에 저장하려는 XML 문자열이 들어 있습니다.

     [!code-vb[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.cs#1)]

2. Word용 문서 수준 프로젝트의 `AddCustomXmlPartToDocument` 클래스에 `ThisDocument` 메서드를 추가합니다.

3. 프로젝트의 다른 코드에서 메서드를 호출합니다. 예를 들어 사용자가 문서를 열 때 사용자 지정 XML 부분을 만들려면 `ThisDocument_Startup` 이벤트 처리기에서 메서드를 호출합니다.

## <a name="robust-programming"></a>강력한 프로그래밍
 간단한 설명을 위해 이 예제에서는 메서드에서 지역 변수로 정의된 XML 문자열을 사용합니다. 일반적으로 파일 또는 데이터베이스와 같은 외부 원본에서 XML을 가져와야 합니다.

## <a name="see-also"></a>참고 항목
- [사용자 지정 XML 부분 개요](../vsto/custom-xml-parts-overview.md)
- [방법: VSTO 추가 기능을 사용 하 여 문서에 사용자 지정 XML 부분 추가](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)

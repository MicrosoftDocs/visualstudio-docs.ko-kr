---
title: VSTO 추가 기능을 사용 하 여 문서에 사용자 지정 XML 부분 추가
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- PowerPoint [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
- application-level add-ins [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 92c00ea69069b7374f5f595cc6f198aac23d1f91
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538296"
---
# <a name="how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins"></a>방법: VSTO 추가 기능을 사용 하 여 문서에 사용자 지정 XML 부분 추가
  VSTO 추가 기능에서 사용자 지정 XML 부분을 만들어 다음과 같은 형식의 문서에 XML 데이터를 저장할 수 있습니다.

- Microsoft Office Excel 통합 문서

- Microsoft Office Word 문서

- Microsoft Office PowerPoint 프레젠테이션

  자세한 내용은 [사용자 지정 XML 부분 개요](../vsto/custom-xml-parts-overview.md)를 참조 하세요.

  **적용 대상:** 이 항목의 정보는 Excel, PowerPoint 및 Word의 애플리케이션 수준 프로젝트에 적용됩니다. 자세한 내용은 [Office 응용 프로그램 및 프로젝트 형식에 따라 사용 가능한 기능](../vsto/features-available-by-office-application-and-project-type.md)을 참조 하세요.

## <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Excel 통합 문서에 사용자 지정 XML 부분을 추가하려면

1. 통합 문서의 <xref:Microsoft.Office.Core.CustomXMLPart> 컬렉션에 새 <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> 개체를 추가합니다. <xref:Microsoft.Office.Core.CustomXMLPart> 에는 통합 문서에 저장하려는 XML 문자열이 들어 있습니다.

     다음 코드 예제에서는 지정된 통합 문서에 사용자 지정 XML 부분을 추가합니다.

     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/VisualBasic/trin_addcustomxmlpartexcelapplevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelAppLevel/ThisAddIn.cs#1)]

2. `AddCustomXmlPartToWorkbook` `ThisAddIn` EXCEL 용 VSTO 추가 기능 프로젝트의 클래스에 메서드를 추가 합니다.

3. 프로젝트의 다른 코드에서 메서드를 호출합니다. 예를 들어 사용자가 통합 문서를 열 때 사용자 지정 XML 부분을 만들려면 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> 이벤트에 대한 이벤트 처리기에서 메서드를 호출합니다.

## <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Word 문서에 사용자 지정 XML 부분을 추가하려면

1. 문서의 <xref:Microsoft.Office.Core.CustomXMLPart> 컬렉션에 새 <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> 개체를 추가합니다. <xref:Microsoft.Office.Core.CustomXMLPart> 에는 문서에 저장하려는 XML 문자열이 들어 있습니다.

     다음 코드 예제에서는 지정된 문서에 사용자 지정 XML 부분을 추가합니다.

     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.cs#1)]

2. `AddCustomXmlPartToDocument` `ThisAddIn` WORD 용 VSTO 추가 기능 프로젝트의 클래스에 메서드를 추가 합니다.

3. 프로젝트의 다른 코드에서 메서드를 호출합니다. 예를 들어 사용자가 문서를 열 때 사용자 지정 XML 부분을 만들려면 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> 이벤트에 대한 이벤트 처리기에서 메서드를 호출합니다.

## <a name="to-add-a-custom-xml-part-to-a-powerpoint-presentation"></a>PowerPoint 프레젠테이션에 사용자 지정 XML 부분을 추가하려면

1. <xref:Microsoft.Office.Core.CustomXMLPart>프레젠테이션의 [Microsoft. _Presentation. CustomXMLParts](/previous-versions/office/developer/office-2010/ff760806%28v%3doffice.14%29) 컬렉션에 새 개체를 추가 합니다. <xref:Microsoft.Office.Core.CustomXMLPart> 에는 프레젠테이션에 저장하려는 XML 문자열이 들어 있습니다.

     다음 코드 예제에서는 지정된 프레젠테이션에 사용자 지정 XML 부분을 추가합니다.

     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.vb#1)]

2. `AddCustomXmlPartToPresentation` `ThisAddIn` POWERPOINT 용 VSTO 추가 기능 프로젝트의 클래스에 메서드를 추가 합니다.

3. 프로젝트의 다른 코드에서 메서드를 호출합니다. 예를 들어 사용자가 프레젠테이션을 열 때 사용자 지정 XML 부분을 만들려면 [AfterPresentationOpen 이벤트 EApplication_Event](/previous-versions/office/developer/office-2010/ff762843(v=office.14)) 에 대 한 이벤트 처리기에서 메서드를 호출 합니다.

## <a name="robust-programming"></a>강력한 프로그래밍
 간단한 설명을 위해 이 예제에서는 메서드에서 지역 변수로 정의된 XML 문자열을 사용합니다. 일반적으로 파일 또는 데이터베이스와 같은 외부 원본에서 XML을 가져와야 합니다.

## <a name="see-also"></a>참고 항목
- [사용자 지정 XML 부분 개요](../vsto/custom-xml-parts-overview.md)
- [방법: 문서 수준 사용자 지정에 사용자 지정 XML 부분 추가](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)

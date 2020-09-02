---
title: '방법: Visual Studio 내에서 워크시트에 스키마 매핑'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c8a0437b940953e89e24969314f63df34d223496
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538140"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>방법: Visual Studio 내에서 워크시트에 스키마 매핑
  워크시트가 Visual Studio에서 열려 있는 동안에는 XML 스키마를 워크시트에 매핑할 수 있습니다. Visual Studio 외부에서 통합 문서를 열 때 사용 하는 것과 동일한 Microsoft Office Excel 도구를 사용 합니다. Excel 솔루션을 만들기 전이나 후에 워크시트에 스키마를 매핑 하는지 여부에 관계 없이 Office 프로젝트는 동일한 개체를 만듭니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Excel 솔루션에서는 다중 파트 XML 스키마를 사용할 수 없습니다.

## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Visual Studio에서 XML 스키마를 Excel 워크시트에 매핑하려면

1. Visual Studio 내에서 Excel 통합 문서 또는 템플릿 프로젝트를 엽니다.

2. 워크시트를 클릭 하 여 디자이너에 포커스를 이동 합니다.

3. 리본에서 **개발자** 탭을 클릭합니다.

    > [!NOTE]
    > **개발자** 탭이 표시되지 않는 경우 먼저 개발자 탭을 표시해야 합니다. 자세한 내용은 [방법: 리본 메뉴에 개발자 탭 표시](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)를 참조 하세요.

4. **XML** 그룹에서 **원본**을 클릭 합니다.

     **XML 소스** 창이 열립니다.

5. **Xml 원본** 창에서 **xml 맵**을 클릭 합니다.

     **XML 맵** 대화 상자가 열립니다.

6. **XML 맵** 대화 상자에서 **추가**를 클릭 합니다.

7. 스키마 파일을 찾아 선택한 다음 **열기**를 클릭 합니다.

8. **확인**을 클릭합니다.

     스키마는 **XML 원본** 창에 표시 됩니다. 프로젝트에서 형식화 된는 <xref:System.Data.DataSet> 스키마를 기반으로 생성 되 고 <xref:System.Windows.Forms.BindingSource> 가 만들어집니다.

9. **XML 소스** 창에서 해당 컨트롤을 만들 위치에 요소를 끌어 놓습니다.

     반복 되지 않는 스키마 요소를 끌면 Office 프로젝트에서에 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 자동으로 바인딩되는 컨트롤이 생성 됩니다 <xref:System.Windows.Forms.BindingSource> .

     반복 스키마 요소를 끌면 Office 프로젝트에서 <xref:Microsoft.Office.Tools.Excel.ListObject> 데이터 소스에 자동으로 바인딩되지 않는 컨트롤이 생성 됩니다. 자세한 내용은 [문서 수준 사용자 지정의 XML 스키마 및 데이터](../vsto/xml-schemas-and-data-in-document-level-customizations.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [방법: Visual Studio 내부의 Word 문서에 스키마 매핑](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [문서 수준 사용자 지정의 XML 스키마 및 데이터](../vsto/xml-schemas-and-data-in-document-level-customizations.md)

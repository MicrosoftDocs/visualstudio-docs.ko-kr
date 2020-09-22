---
title: 문서 수준 사용자 지정의 XML 스키마 및 데이터
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio]
- schemas [Office development in Visual Studio]
- XML [Office development in Visual Studio], XML schemas
- XML schemas [Office development in Visual Studio], about XML schemas and data
- Office development in Visual Studio, XML
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eb8bc9b9d3149112517d893cd3a704826b6d92d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841839"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>문서 수준 사용자 지정의 XML 스키마 및 데이터
  **중요** Microsoft word와 관련 하 여이 항목에서 설명 하는 정보는 microsoft word에서 사용자 지정 XML과 관련 된 특정 기능의 구현을 제거 했을 때 미국 및 해당 지역 외부에 있거나 microsoft에서 실행 되는 프로그램 (1 월 2010 이전에 Microsoft에서 사용이 허가 된 Microsoft Word 제품)의 혜택 및 사용을 위해서만 제공 됩니다. Microsoft Word에 대 한이 정보는 microsoft word 제품이 2010 년 1 월 10 일 이후 Microsoft에서 사용이 허가 된 Microsoft Word 제품,에서 실행 되는 프로그램을 개발 하거나 사용 하는 미국 또는 지역에 있는 개인 또는 조직에서 읽거나 사용할 수 없습니다. 이러한 제품은 해당 날짜 이전에 사용이 허가 된 제품과 동일 하 게 작동 하지 않습니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Excel 및 Microsoft Office Word Microsoft Office 문서에 스키마를 매핑하는 기능을 제공 합니다. 이 기능을 통해 문서에서 XML 데이터를 가져오거나 내보낼 수 있습니다.

 Visual Studio에서는 문서 수준 사용자 지정의 매핑된 스키마 요소를 프로그래밍 모델의 컨트롤로 노출 합니다. Excel의 경우, Visual Studio는 데이터베이스, 웹 서비스 및 개체의 데이터에 컨트롤을 바인딩하는 기능을 추가 합니다. Word 및 Excel의 경우 Visual Studio에서 스키마 매핑 문서와 함께 사용 하 여 솔루션에 대 한 향상 된 최종 사용자 환경을 만들 수 있는 작업 창에 대 한 지원을 추가 합니다. 자세한 내용은 [작업 창 개요](../vsto/actions-pane-overview.md)를 참조 하세요.

> [!NOTE]
> Excel 솔루션에서는 다중 파트 XML 스키마를 사용할 수 없습니다.

## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Excel 통합 문서에 스키마가 연결 될 때 생성 되는 개체
 통합 문서에 스키마를 연결 하면 Visual Studio에서 자동으로 여러 개체를 만들어 프로젝트에 추가 합니다. 이러한 개체는 Excel에서 관리 되므로 Visual Studio tools를 사용 하 여 삭제 하면 안 됩니다. 이를 삭제 하려면 워크시트에서 매핑된 요소를 제거 하거나 Excel 도구를 사용 하 여 스키마를 분리 합니다.

 두 가지 주요 개체가 있습니다.

- XML 스키마 (XSD 파일) Visual Studio는 통합 문서의 모든 스키마에 대해 프로젝트에 스키마를 추가 합니다. **솔루션 탐색기**에서 XSD 확장이 있는 프로젝트 항목으로 나타납니다.

- 형식화된 <xref:System.Data.DataSet> 클래스. 이 클래스는 스키마를 기반으로 만들어집니다. 이 dataset 클래스는 **클래스 뷰**에서 볼 수 있습니다.

## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>스키마 요소를 Excel 워크시트에 매핑할 때 생성 되는 개체
 **XML 원본** 작업창의 스키마 요소를 워크시트에 매핑하면 Visual Studio에서 자동으로 여러 개체를 만들어 프로젝트에 추가 합니다.

- 제어가. 통합 문서의 매핑된 모든 개체에 대해 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 프로그래밍 모델에서 반복 되지 않는 스키마 요소에 대 한 컨트롤 또는 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤 (반복 스키마 요소의 경우)이 만들어집니다. <xref:Microsoft.Office.Tools.Excel.ListObject>컨트롤은 통합 문서에서 매핑 및 매핑된 개체를 삭제 하는 방법 으로만 삭제할 수 있습니다. 컨트롤에 대 한 자세한 내용은 [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)를 참조 하세요.

- BindingSource. <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>반복 되지 않는 스키마 요소를 워크시트에 매핑하여를 만들면 <xref:System.Windows.Forms.BindingSource> 이 만들어지고 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 컨트롤이에 바인딩됩니다 <xref:System.Windows.Forms.BindingSource> . 를 <xref:System.Windows.Forms.BindingSource> 문서에 매핑된 스키마 (예: 생성 된 형식화 된 클래스의 인스턴스)와 일치 하는 데이터 소스의 인스턴스에 바인딩해야 합니다 <xref:System.Data.DataSet> . <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> **속성** 창에 노출 되는 및 속성을 설정 하 여 바인딩을 만듭니다.

    > [!NOTE]
    > 는 <xref:System.Windows.Forms.BindingSource> 개체에 대해 생성 되지 않습니다 <xref:Microsoft.Office.Tools.Excel.ListObject> . <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> **속성** 창에서 및 속성을 설정 하 여를 데이터 원본에 수동으로 바인딩해야 합니다.

### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Office 매핑된 스키마 및 Visual Studio 데이터 소스 창
 Office 및 Visual Studio **데이터 소스** 창의 매핑된 스키마 기능을 모두 통해 Excel 워크시트의 데이터를 보고 하거나 편집할 수 있습니다. 두 경우 모두 데이터 요소를 Excel 워크시트로 끌어올 수 있습니다. 두 메서드는를 통해 데이터 <xref:System.Windows.Forms.BindingSource> 소스에 또는 웹 서비스와 같은 데이터에 바인딩된 컨트롤을 만듭니다 <xref:System.Data.DataSet> .

> [!NOTE]
> 반복 스키마 요소를 워크시트에 매핑하면 Visual Studio에서를 만듭니다 <xref:Microsoft.Office.Tools.Excel.ListObject> . 는를 <xref:Microsoft.Office.Tools.Excel.ListObject> 통해 데이터에 자동으로 바인딩되지 않습니다 <xref:System.Windows.Forms.BindingSource> . <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> **속성** 창에서 및 속성을 설정 하 여를 데이터 원본에 수동으로 바인딩해야 합니다.

 다음 표에서는 두 방법 간의 차이점을 보여 줍니다.

|XML 스키마|데이터 소스 창|
|----------------|-------------------------|
|Office 인터페이스를 사용 합니다.|Visual Studio에서 **데이터 소스** 창을 사용 합니다.|
|XML 파일에서 데이터를 가져오고 내보내는 기본 제공 Office 기능을 사용 하도록 설정 합니다.|가져오기 및 내보내기 기능을 프로그래밍 방식으로 제공 해야 합니다.|
|생성 된 컨트롤을 데이터로 채우는 코드를 작성 해야 합니다.|**데이터 소스** 창에서 추가 된 컨트롤에는 데이터베이스 서버를 사용할 때 필요한 연결 문자열과 함께 자동으로 생성 되는 코드가 있습니다.|

## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Word 문서에 스키마가 연결 된 경우의 동작
 문서 수준 Office 프로젝트에서 사용 되는 Word 문서에 스키마를 연결 하는 경우에는 데이터 개체가 생성 되지 않습니다. 그러나 스키마 요소를 문서에 매핑하면 컨트롤이 생성 됩니다. 컨트롤의 형식은 매핑하는 요소의 유형에 따라 달라 집니다. 반복 <xref:Microsoft.Office.Tools.Word.XMLNodes> 되는 요소는 컨트롤을 생성 하 고 반복 되지 않는 요소는 컨트롤을 생성 <xref:Microsoft.Office.Tools.Word.XMLNode> 합니다. 자세한 내용은 [XMLNodes control](../vsto/xmlnodes-control.md) 및 [XMLNode control](../vsto/xmlnode-control.md)을 참조 하세요.

## <a name="deployment-of-solutions-that-include-xml-schemas"></a>XML 스키마를 포함 하는 솔루션 배포
 문서에 매핑된 XML 스키마를 사용 하는 솔루션을 배포 하려면 설치 관리자를 만들어야 합니다. 설치 관리자가 스키마 라이브러리의 스키마를 사용자 컴퓨터에 등록 해야 합니다. 스키마를 등록 하지 않으면 사용자가 문서를 열 때 문서에 있는 요소를 기준으로 임시 스키마를 생성 하므로 솔루션은 계속 작동 합니다. 그러나 사용자는 프로젝트를 만드는 데 사용 된 스키마를 저장 하거나 유효성 검사를 수행할 수 없습니다. 설치 관리자에 대 한 자세한 내용은 [응용 프로그램, 서비스 및 구성 요소 배포](../deployment/deploying-applications-services-and-components.md)를 참조 하세요.

 프로젝트에 코드를 추가 하 여 스키마가 라이브러리에 있고 등록 되었는지 확인할 수도 있습니다. 그렇지 않으면 사용자에 게 경고할 수 있습니다.

 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]

## <a name="see-also"></a>참고 항목

- [방법: Visual Studio 내부의 Word 문서에 스키마 매핑](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [방법: Visual Studio 내에서 워크시트에 스키마 매핑](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)

---
title: '방법: 워크시트에 XMLMappedRange 컨트롤 추가'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1d69e705e8f537ba3636422ad6883a7633e03322
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544887"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>방법: 워크시트에 XMLMappedRange 컨트롤 추가
  XML 요소를 Excel Microsoft Office의 셀에 매핑하면 Visual Studio에서 자동으로 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 컨트롤을 워크시트에 추가 합니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>컨트롤은 **도구 상자** 또는 **데이터 소스** 창에서 사용할 수 없습니다. 또한 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 프로그래밍 방식으로 컨트롤을 만들 수 없습니다.

## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>워크시트에 XMLMappedRange 컨트롤을 추가 하려면

1. Visual Studio 디자이너에서 Excel 통합 문서를 엽니다.

2. 컨트롤을 추가 하려는 워크시트를 엽니다.

3. **개발자** 탭에서 **원본**을 클릭 합니다.

    > [!NOTE]
    > 리본 메뉴에 **개발자** 탭이 표시 되지 않는 경우 사용 하도록 설정 해야 합니다. 자세한 내용은 [방법: 리본 메뉴에 개발자 탭 표시](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)를 참조 하세요.

     **XML 원본** 작업 창이 표시 됩니다.

4. **Xml 원본** 작업 창에서 **xml 맵**을 클릭 합니다.

5. **XML 맵** 대화 상자에서 **추가**를 클릭 합니다.

     **XML 원본** 대화 상자가 나타납니다.

6. **Xml 원본** 대화 상자에서 xml 스키마를 선택 하 고 **열기**를 클릭 합니다.

     스키마가 **XML 맵** 대화 상자에 추가 됩니다.

7. **XML 맵** 대화 상자에서 **확인**을 클릭 합니다.

8. 요소를 **XML 원본** 작업창에서 워크시트의 셀로 끕니다.

     <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>이 만들어지고 프로젝트에 추가 됩니다.

    > [!NOTE]
    > **XML 원본** 작업창에서 부모 요소를 끌면 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤이 생성 됩니다.

## <a name="see-also"></a>추가 정보
- [XmlMappedRange 컨트롤](../vsto/xmlmappedrange-control.md)
- [확장 된 개체를 사용 하 여 Excel 자동화](../vsto/automating-excel-by-using-extended-objects.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍에 대 한 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [방법: Visual Studio 내에서 워크시트에 스키마 매핑](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)

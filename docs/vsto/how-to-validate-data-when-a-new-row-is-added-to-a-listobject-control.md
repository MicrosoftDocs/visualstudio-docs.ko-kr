---
title: ListObject 컨트롤에 새 행을 추가할 때 데이터 유효성 검사
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2b9ed8428f9dd0325678cb91a847609aed76f9b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85541169"
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>방법: ListObject 컨트롤에 새 행을 추가할 때 데이터 유효성 검사
  사용자는 데이터에 바인딩된 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤에 새 행을 추가할 수 있습니다. 데이터 원본에 대한 변경 내용을 커밋하기 전에 사용자 데이터의 유효성을 확인할 수 있습니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="data-validation"></a>데이터 유효성 검사
 데이터에 바인딩된 <xref:Microsoft.Office.Tools.Excel.ListObject> 에 행을 추가할 때마다 <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> 이벤트가 발생합니다. 데이터 유효성 검사를 수행하도록 이 이벤트를 처리할 수 있습니다. 예를 들어 응용 프로그램에서 18 ~ 65 사이의 직원만 데이터 원본에 추가할 수 있도록 요구 하는 경우 행이 추가 되기 전에 입력 한 나이가 해당 범위에 속하는지 확인 합니다.

> [!NOTE]
> 클라이언트뿐 아니라 서버에서의 사용자 입력도 항상 확인해야 합니다. 자세한 내용은 [클라이언트 응용 프로그램 보안](/dotnet/framework/data/adonet/secure-client-applications)을 참조 하세요.

### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>데이터 바인딩된 ListObject에 새 행을 추가할 때 데이터 유효성을 검사하려면

1. 클래스 수준에서 ID 및 <xref:System.Data.DataTable> 에 대한 변수를 만듭니다.

     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#8)]

2. 새을 만들고 <xref:System.Data.DataTable> `Startup` `Sheet1` 클래스 (문서 수준 프로젝트) 또는 `ThisAddIn` 클래스 (VSTO 추가 기능 프로젝트)의 이벤트 처리기에 샘플 열과 데이터를 추가 합니다.

     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#9)]

3. `list1_BeforeAddDataBoundRow` 이벤트 처리기에 코드를 추가하여 입력된 나이가 허용 가능한 범위 내에 포함되는지 확인합니다.

     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#10)]

## <a name="compile-the-code"></a>코드 컴파일
 이 코드 예제에서는 이 코드가 표시되는 워크시트에 <xref:Microsoft.Office.Tools.Excel.ListObject> 이라는 기존 `list1` 가 있는 것으로 간주합니다.

## <a name="see-also"></a>추가 정보
- [런타임에 VSTO 추가 기능에서 Word 문서 및 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office 문서의 컨트롤](../vsto/controls-on-office-documents.md)
- [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [ListObject 컨트롤](../vsto/listobject-control.md)
- [확장 된 개체를 사용 하 여 Excel 자동화](../vsto/automating-excel-by-using-extended-objects.md)
- [방법: 데이터에 ListObject 열 매핑](../vsto/how-to-map-listobject-columns-to-data.md)

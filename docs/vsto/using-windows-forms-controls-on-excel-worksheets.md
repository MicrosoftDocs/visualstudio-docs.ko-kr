---
title: Excel 워크시트에서 Windows Forms 컨트롤 사용
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 032ee551ff04590ccdb8744c1274b137dec0b756
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62982315"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>Excel 워크시트에서 Windows Forms 컨트롤 사용
  Windows Forms에 컨트롤을 추가 하는 것과 같은 방식으로 Microsoft Office Excel 통합 문서에 Windows Forms 컨트롤을 추가할 수 있습니다. 문서에서 컨트롤을 사용 하는 방법에 대 한 일반적인 내용은 [Office 문서의 컨트롤 Windows Forms 개요](../vsto/windows-forms-controls-on-office-documents-overview.md)를 참조 하세요.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="control-considerations-for-excel"></a>Excel에 대 한 컨트롤 고려 사항
 Excel과 관련 된 몇 가지 고려 사항이 있습니다.

### <a name="match-control-size-to-cell-size"></a>컨트롤 크기를 셀 크기와 일치
 부모 셀의 크기가 변경될 때 자동으로 컨트롤의 크기가 조정되도록 설정할 수 있습니다. 자세한 내용은 [방법: 워크시트 셀 내 컨트롤 크기 조정](../vsto/how-to-resize-controls-within-worksheet-cells.md)을 참조 하세요.

### <a name="add-components-that-are-shared-by-all-worksheets"></a>모든 워크시트에서 공유 하는 구성 요소 추가
 <xref:System.Data.DataSet>등 모든 워크시트에서 공유하려는 구성 요소는 워크시트 대신 통합 문서 디자이너에 추가할 수 있습니다. 이러한 구성 요소는 구성 요소 트레이에 표시됩니다.

### <a name="formula-for-embedding-controls"></a>컨트롤 포함에 대 한 수식
 Excel에서 컨트롤을 선택하는 경우 **수식 입력줄** 에 **=EMBED("WinForms.Control.Host","")** 가 표시됩니다. 이 텍스트는 필요하며 삭제하면 안 됩니다.

## <a name="see-also"></a>추가 정보
- [방법: 워크시트 셀에서 컨트롤 크기 조정](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [방법: 인쇄할 때 워크시트에서 컨트롤 숨기기](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [연습: CheckBox 컨트롤을 사용 하 여 워크시트 서식 변경](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [연습: 워크시트에서 단추를 사용 하 여 텍스트 상자에 텍스트 표시](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [연습: 워크시트에서 라디오 단추를 사용 하 여 차트 업데이트](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)

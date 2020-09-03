---
title: '방법: 워크시트 셀에서 컨트롤 크기 조정'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f2d22973e13ee77b66de303041f8b6a765b4b93a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545875"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>방법: 워크시트 셀에서 컨트롤 크기 조정
  워크시트의 열 이나 행의 크기를 조정 하면 셀의 모든 호스트 컨트롤 크기가 자동으로 조정 되는 셀의 높이나 너비에 맞게 자동으로 조정 됩니다. Windows Forms 컨트롤은 기본적으로 자동으로 크기가 조정 되지 않습니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 디자인 타임에 컨트롤을 추가 하는 경우 각 컨트롤에 대 한 위치 지정 옵션을 설정 해야 합니다.

 프로그래밍 방식으로 Windows Forms 컨트롤을 추가 하 고 범위 인수를 제공 하는 경우 범위 내의 셀 크기가 조정 되 면 컨트롤의 크기가 자동으로 조정 됩니다. 자세한 내용은 [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)를 참조 하세요.

## <a name="resize-controls-at-design-time"></a>디자인 타임에 컨트롤 크기 조정

### <a name="to-make-controls-resize-with-cells-at-design-time"></a>디자인 타임에 컨트롤의 크기를 셀 크기에 맞게 지정 하려면

1. **도구 상자**에서 Windows Forms 컨트롤을 워크시트로 끌어 옵니다.

2. 컨트롤을 마우스 오른쪽 단추로 클릭 하 고 **컨트롤 서식**을 클릭 합니다.

3. **컨트롤 서식 지정** 대화 상자에서 **속성** 탭을 클릭 합니다.

4. **개체 위치 지정**에서 **셀로 이동 및 크기 조정** 옵션을 선택한 다음 **확인**을 클릭 합니다.

     컨트롤을 포함 하는 셀의 크기를 조정 하는 경우 컨트롤은 셀에 맞게 크기가 조정 됩니다.

## <a name="resize-controls-at-run-time"></a>런타임에 컨트롤 크기 조정
 런타임에 Windows Forms 컨트롤을 추가 하 고 컨트롤의 위치로를 전달 하는 경우 <xref:Microsoft.Office.Interop.Excel.Range> 범위를 포함 하는 워크시트 셀의 크기가 조정 되 면 컨트롤의 크기가 자동으로 조정 됩니다.

### <a name="to-make-controls-resize-with-cells-at-run-time"></a>런타임에 셀을 사용 하 여 컨트롤 크기를 조정 하려면

1. 범위 A1에 컨트롤을 추가 합니다.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]

     컨트롤을 포함 하는 셀의 크기를 조정 하는 경우 컨트롤은 셀에 맞게 크기가 조정 됩니다.

## <a name="reset-control-placement"></a>컨트롤 배치 다시 설정
 `Placement`속성을 다음 값 중 하나로 설정 하 여 컨트롤의 배치와 크기 조정을 다시 설정할 수 있습니다 <xref:Microsoft.Office.Interop.Excel.XlPlacement> .

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>

### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>셀의 크기를 조정 하거나 이동 하지 않도록 컨트롤의 동작을 변경 하려면

1. 컨트롤의 배치 속성을 호출 하 고 값을로 설정 <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating> 합니다.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]

## <a name="see-also"></a>추가 정보
- [Office 문서의 컨트롤](../vsto/controls-on-office-documents.md)
- [방법: Office 문서에 Windows Forms 컨트롤 추가](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [방법: 인쇄할 때 워크시트에서 컨트롤 숨기기](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Office 문서에서 Windows Forms 컨트롤의 제한 사항](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)

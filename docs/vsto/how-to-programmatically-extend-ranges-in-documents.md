---
title: '방법: 프로그래밍 방식으로 문서의 범위 확장'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, extending
- documents [Office development in Visual Studio], extending ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 35ef0ea0352141f18945632f996237c2d9d90204
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547422"
---
# <a name="how-to-programmatically-extend-ranges-in-documents"></a>방법: 프로그래밍 방식으로 문서의 범위 확장
  Microsoft Office Word 문서에서 <xref:Microsoft.Office.Interop.Word.Range> 개체를 정의한 후 <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> 및 <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> 메서드를 사용하여 해당 개체의 시작점과 끝점을 변경합니다. <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A>및 <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> 메서드는 두 개의 인수, 즉 *Unit* 및 *Count*를 사용 합니다. *Count* 인수는 이동할 단위의 수이 고, *Unit* 인수는 다음 값 중 하나일 수 있습니다 <xref:Microsoft.Office.Interop.Word.WdUnits> .

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCharacter>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdWord>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSentence>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdParagraph>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSection>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdStory>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCell>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdColumn>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdRow>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdTable>

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

  다음 예제에서 일곱 개의 문자로 구성된 범위를 정의합니다. 그런 다음 범위의 시작 위치를 원래 시작 위치에서 일곱 문자 뒤로 이동합니다. 범위의 끝 위치는 원래 시작 위치에서 일곱 문자 뒤에 있으므로 범위를 변경한 결과에는 문자가 포함되지 않습니다. 그런 다음 이 코드에서는 끝 위치를 현재 끝 위치에서 일곱 문자 뒤로 이동합니다.

## <a name="to-extend-a-range"></a>범위를 확장하려면

1. 문자의 범위를 정의합니다. 자세한 내용은 [방법: 프로그래밍 방식으로 문서에서 범위 정의 및 선택](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)을 참조 하세요.

     다음 코드 예제는 문서 수준 사용자 지정에서 사용할 수 있습니다.

     [!code-vb[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#39)]

     다음 코드 예제는 VSTO 추가 기능에서 사용할 수 있습니다. 이 예제에서는 활성 문서를 사용합니다.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#39)]

2. <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> 개체의 <xref:Microsoft.Office.Interop.Word.Range> 메서드를 사용하여 범위의 시작 위치를 옮깁니다.

     [!code-vb[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#40)]
     [!code-csharp[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#40)]

3. <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> 개체의 <xref:Microsoft.Office.Interop.Word.Range> 메서드를 사용하여 범위의 끝 위치를 옮깁니다.

     [!code-vb[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#41)]
     [!code-csharp[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#41)]

## <a name="document-level-customization-code"></a>문서 수준 사용자 지정 코드

### <a name="to-extend-a-range-in-a-document-level-customization"></a>문서 수준 사용자 지정의 범위를 확장하려면

1. 다음 예제에서는 문서 수준 사용자 지정의 전체 코드를 보여 줍니다. 이 코드를 사용하려면 프로젝트의 `ThisDocument` 클래스에서 실행합니다.

     [!code-vb[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#38)]

## <a name="vsto-add-in-code"></a>VSTO 추가 기능 코드

### <a name="to-extend-a-range-in-an-application-level-vsto-add-in"></a>애플리케이션 수준 VSTO 추가 기능의 범위를 확장하려면

1. 다음 예제에서는 VSTO 추가 기능의 전체 코드를 보여 줍니다. 이 코드를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#38)]

## <a name="see-also"></a>참고 항목
- [방법: 프로그래밍 방식으로 Word 문서의 범위 다시 설정](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [방법: 프로그래밍 방식으로 문서의 범위 또는 선택 영역 축소](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [방법: 프로그래밍 방식으로 문서의 범위 정의 및 선택](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [방법: 프로그래밍 방식으로 범위의 시작 및 끝 문자 검색](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [방법: 프로그래밍 방식으로 범위를 만들 때 단락 표시 제외](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)

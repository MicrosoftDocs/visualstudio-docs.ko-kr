---
title: '방법: 프로그래밍 방식으로 문서 닫기'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing
- Word [Office development in Visual Studio], closing documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 18dc4099f4c1df17efbe2dd3c213332bb73b52c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547461"
---
# <a name="how-to-programmatically-close-documents"></a>방법: 프로그래밍 방식으로 문서 닫기
  활성 문서를 닫거나 닫을 문서를 지정할 수 있습니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="close-the-active-document"></a>활성 문서 닫기
 활성 문서를 닫는 절차에는 문서 수준 사용자 지정 및 VSTO 추가 기능에 대해 각각 하나씩, 두 가지가 있습니다.

### <a name="to-close-the-active-document-in-a-document-level-customization"></a>문서 수준 사용자 지정에서 활성 문서를 닫으려면

1. 프로젝트에서 <xref:Microsoft.Office.Tools.Word.Document.Close%2A> 클래스의 `ThisDocument` 메서드를 호출하여 사용자 지정과 연결된 문서를 닫습니다. 다음 코드 예제를 사용하려면 `ThisDocument` 클래스에서 실행합니다.

    > [!NOTE]
    > 이 예제에서는 <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> 값을 *SaveChanges* 매개 변수에 전달하여 변경 내용을 저장하거나 사용자에게 메시지를 표시하지 않고 닫습니다.

     [!code-vb[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#3)]

### <a name="to-close-the-active-document-in-a-vsto-add-in"></a>VSTO 추가 기능에서 활성 문서를 닫으려면

1. <xref:Microsoft.Office.Interop.Word._Document.Close%2A> 속성의 <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> 메서드를 호출하여 활성 문서를 닫습니다. 다음 코드 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

    > [!NOTE]
    > 이 예제에서는 <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> 값을 *SaveChanges* 매개 변수에 전달하여 변경 내용을 저장하거나 사용자에게 메시지를 표시하지 않고 닫습니다.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#3)]

## <a name="close-a-document-that-you-specify-by-name"></a>이름으로 지정한 문서를 닫습니다.
 이름으로 지정한 문서를 닫는 방법은 VSTO 추가 기능과 문서 수준 사용자 지정에서 동일합니다.

### <a name="to-close-a-document-that-you-specify-by-name"></a>이름으로 지정한 문서를 닫으려면

1. <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> 컬렉션에 대한 인수로 문서 이름을 지정하고 <xref:Microsoft.Office.Interop.Word._Document.Close%2A> 메서드를 호출합니다. 다음 코드 예제에서는 **NewDocument** 라는 문서가 Word에서 열려 있다고 가정합니다.

    > [!NOTE]
    > 이 예제에서는 <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> 값을 *SaveChanges* 매개 변수에 전달하여 변경 내용을 저장하거나 사용자에게 메시지를 표시하지 않고 닫습니다.

     [!code-vb[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#4)]

## <a name="see-also"></a>추가 정보
- [방법: 프로그래밍 방식으로 기존 문서 열기](../vsto/how-to-programmatically-open-existing-documents.md)
- [방법: 프로그래밍 방식으로 문서 저장](../vsto/how-to-programmatically-save-documents.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍에 대 한 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)

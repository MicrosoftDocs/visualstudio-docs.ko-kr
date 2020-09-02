---
title: '방법: 프로그래밍 방식으로 Word의 기본 제공 대화 상자 사용'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2c3273b22d98be1c22cf0c8cea2cb57e277b9b48
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537620"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>방법: 프로그래밍 방식으로 Word의 기본 제공 대화 상자 사용
  Microsoft Office Word를 사용할 때 사용자 입력에 대 한 대화 상자를 표시 해야 하는 경우가 있습니다. 직접 만들 수도 있지만 개체의 컬렉션에 노출 되는 Word에서 기본 제공 대화 상자를 사용 하는 방법을 사용할 수도 있습니다 <xref:Microsoft.Office.Interop.Word.Dialogs> <xref:Microsoft.Office.Interop.Word.Application> . 이를 통해 열거형으로 표시 되는 기본 제공 대화 상자를 200 이상 액세스할 수 있습니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="display-dialog-boxes"></a>대화 상자 표시
 대화 상자를 표시 하려면 열거형의 값 중 하나를 사용 <xref:Microsoft.Office.Interop.Word.WdWordDialog> 하 여 <xref:Microsoft.Office.Interop.Word.Dialog> 표시 하려는 대화 상자를 나타내는 개체를 만듭니다. 그런 다음 <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> 개체의 메서드를 호출 합니다 <xref:Microsoft.Office.Interop.Word.Dialog> .

 다음 코드 예제에서는 **파일 열기** 대화 상자를 표시 하는 방법을 보여 줍니다. 이 예제를 사용 하려면 `ThisDocument` `ThisAddIn` 프로젝트의 또는 클래스에서 실행 합니다.

 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]

### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>런타임에 바인딩을 통해 사용할 수 있는 대화 상자 멤버 액세스
 Word에서 대화 상자의 일부 속성 및 메서드는 런타임에 바인딩을 통해서만 사용할 수 있습니다. **Option Strict** 가 on 인 Visual Basic 프로젝트에서 리플렉션을 사용 하 여 이러한 멤버에 액세스 해야 합니다. 자세한 내용은 [Office 솔루션의 런타임에 바인딩](../vsto/late-binding-in-office-solutions.md)을 참조 하세요.

 다음 코드 예제에서는 **옵션 Strict** 가 off 인 경우 또는 또는를 대상으로 하는 Visual c # 프로젝트에서 **파일 열기** 대화 Visual Basic 상자의 **Name** 속성을 사용 하는 방법을 보여 줍니다 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . 이 예제를 사용 하려면 `ThisDocument` `ThisAddIn` 프로젝트의 또는 클래스에서 실행 합니다.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 다음 코드 예제에서는 리플렉션을 사용 하 여 **Option Strict** 가 on 인 Visual Basic 프로젝트에서 **파일 열기** 대화 상자의 **이름** 속성에 액세스 하는 방법을 보여 줍니다. 이 예제를 사용 하려면 `ThisDocument` `ThisAddIn` 프로젝트의 또는 클래스에서 실행 합니다.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>추가 정보
- [방법: 프로그래밍 방식으로 숨겨진 모드에서 Word 대화 상자 사용](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Word 개체 모델 개요](../vsto/word-object-model-overview.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
- [Option strict 문](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [리플렉션(C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [리플렉션(Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)

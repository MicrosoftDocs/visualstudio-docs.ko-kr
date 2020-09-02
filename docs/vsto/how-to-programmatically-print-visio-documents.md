---
title: '방법: 프로그래밍 방식으로 Visio 문서 인쇄'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0e31a55e49d42311b5ec5fff82769584cc55ce09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537802"
---
# <a name="how-to-programmatically-print-visio-documents"></a>방법: 프로그래밍 방식으로 Visio 문서 인쇄
  전체 Microsoft Office Visio 문서 또는 특정 페이지만 인쇄할 수 있습니다.

 인쇄 방법에 대한 자세한 내용은 VBA 참조 설명서에서 [Microsoft.Office.Interop.Visio.Document.Print](/office/vba/api/Visio.Document.Print) 메서드 및 [Microsoft.Office.Interop.Visio.Page.Print](/office/vba/api/Visio.Page.Print) 메서드를 참조하세요.

## <a name="print-a-visio-document"></a>Visio 문서 인쇄

### <a name="to-print-a-complete-document"></a>전체 문서를 인쇄하려면

- 인쇄하려는 `Microsoft.Office.Interop.Visio.Document.Print` 개체의 `Microsoft.Office.Interop.Visio.Document` 메서드를 호출합니다.

     다음 코드 예제에서는 활성 문서를 인쇄합니다. 이 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 코드를 실행합니다.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]

## <a name="print-a-page-of-a-visio-document"></a>Visio 문서 페이지 인쇄

### <a name="to-print-a-page-of-a-document"></a>문서 페이지를 인쇄하려면

- 인쇄하려는 `Microsoft.Office.Interop.Visio.Pages.Print` 개체의 `Microsoft.Office.Interop.Visio.Pages` 메서드를 호출합니다.

     다음 코드 예제에서는 활성 문서의 첫 번째 페이지를 인쇄합니다. 이 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 코드를 실행합니다.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>추가 정보
- [Visio 솔루션](../vsto/visio-solutions.md)
- [Visio 개체 모델 개요](../vsto/visio-object-model-overview.md)
- [방법: 프로그래밍 방식으로 새 Visio 문서 만들기](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [방법: 프로그래밍 방식으로 Visio 문서 열기](../vsto/how-to-programmatically-open-visio-documents.md)
- [방법: 프로그래밍 방식으로 Visio 문서 닫기](../vsto/how-to-programmatically-close-visio-documents.md)
- [방법: 프로그래밍 방식으로 Visio 문서 저장](../vsto/how-to-programmatically-save-visio-documents.md)

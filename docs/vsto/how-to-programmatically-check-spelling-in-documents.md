---
title: '방법: 프로그래밍 방식으로 문서에서 맞춤법 검사'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 93ba9d9907135952f7408652bfb36f440d23138d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537854"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>방법: 프로그래밍 방식으로 문서에서 맞춤법 검사
  문서에서 맞춤법을 검사 하려면 메서드를 사용 <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> 합니다. 이 메서드는 제공 된 매개 변수의 철자가 정확한 지 여부를 나타내는 부울 값을 반환 합니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>맞춤법을 검사 하 고 결과를 메시지 상자에 표시 하려면

1. 메서드를 호출 하 <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> 고 텍스트 범위를 전달 하 여 맞춤법 오류를 확인 합니다. 이 코드 예제를 사용하려면 프로젝트의 `ThisDocument` 또는 `ThisAddIn` 클래스에서 실행합니다.

     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]

## <a name="see-also"></a>추가 정보
- [방법: 프로그래밍 방식으로 문서의 범위 정의 및 선택](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)

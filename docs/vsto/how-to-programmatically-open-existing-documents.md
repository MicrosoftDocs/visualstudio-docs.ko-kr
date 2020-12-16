---
title: '방법: 프로그래밍 방식으로 기존 문서 열기'
description: Open 메서드를 사용 하 여 정규화 된 경로 및 파일 이름으로 지정 된 기존 Microsoft Word 문서를 여는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 994afc6f0d8d9bb76aff56097d0a18b8c3f940d9
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525552"
---
# <a name="how-to-programmatically-open-existing-documents"></a>방법: 프로그래밍 방식으로 기존 문서 열기
  메서드는 정규화 <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> 된 경로와 파일 이름으로 지정 된 기존 Microsoft Office Word 문서를 엽니다. 이 메서드는 <xref:Microsoft.Office.Interop.Word.Document> 열린 문서를 나타내는을 반환 합니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-open-a-document"></a>문서를 열려면

- <xref:Microsoft.Office.Interop.Word.Documents.Open%2A>컬렉션의 메서드를 호출 <xref:Microsoft.Office.Interop.Word.Documents> 하 고 문서에 대 한 경로를 제공 합니다.

     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]

## <a name="to-open-a-document-as-read-only"></a>문서를 읽기 전용으로 열려면

- 메서드를 호출 하 고 <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> , 문서에 대 한 경로를 제공 하 고, 메서드 호출에서 *ReadOnly* 인수를 **True** 로 설정 합니다.

     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]

## <a name="compile-the-code"></a>코드 컴파일
 이 코드 예제에는 다음이 필요합니다.

- *NewDocument.doc* 이라는 문서는 C 드라이브의 *Test* 라는 디렉터리에 있어야 합니다.

## <a name="see-also"></a>참고 항목
- [방법: 프로그래밍 방식으로 새 문서 만들기](../vsto/how-to-programmatically-create-new-documents.md)
- [방법: 프로그래밍 방식으로 문서 닫기](../vsto/how-to-programmatically-close-documents.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)

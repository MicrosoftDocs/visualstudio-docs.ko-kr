---
title: '방법: 프로그래밍 방식으로 Visio 문서에 셰이프 추가'
description: 스텐실에서 마스터를 검색 하 고 활성 페이지에서 셰이프를 삭제 하 여 Microsoft Office Visio 문서에 셰이프를 추가 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f5eabd18ac915e6cc10ff05de3d13d0263fa1eee
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828412"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>방법: 프로그래밍 방식으로 Visio 문서에 셰이프 추가
  스텐실에서 마스터를 검색하고 활성 페이지로 셰이프를 끌어 놓아 Microsoft Office Visio 문서에 셰이프를 추가할 수 있습니다.

 자세한 내용은 [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) 메서드, [Microsoft.Office.Interop.Visio.Application.ActivePage](/office/vba/api/Visio.Application.ActivePage) 속성 및 [Microsoft.Office.Interop.Visio.Page.Drop](/office/vba/api/Visio.Page.Drop) 메서드에 대한 VBA 참조 설명서를 참조하세요.

## <a name="add-shapes-to-a-visio-document"></a>Visio 문서에 셰이프 추가

### <a name="to-add-shapes-to-a-visio-document"></a>Visio 문서를 셰이프를 추가하려면

- 문서를 활성화하고 Documents.Masters 컬렉션에서 마스터를 검색하여 활성 문서에 셰이프를 끌어 놓습니다. 인덱스 또는 마스터 이름을 사용하여 마스터를 검색할 수 있습니다.

     다음 코드 예제에서는 빈 Visio 문서를 만든 다음 **기본 셰이프** 스텐실이 도킹된 상태에서 엽니다. 그러면 코드에서 여러 셰이프를 검색하여 활성 페이지에 끌어 놓습니다.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet13":::

## <a name="see-also"></a>참조
- [Visio 솔루션](../vsto/visio-solutions.md)
- [Visio 개체 모델 개요](../vsto/visio-object-model-overview.md)
- [Visio 셰이프 작업](../vsto/working-with-visio-shapes.md)
- [방법: 프로그래밍 방식으로 Visio 문서에서 셰이프 복사 및 붙여넣기](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)

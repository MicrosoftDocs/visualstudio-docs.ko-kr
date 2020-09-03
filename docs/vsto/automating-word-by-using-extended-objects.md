---
title: 확장 된 개체를 사용 하 여 Word 자동화
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], automating
- extended objects [Office development in Visual Studio], Word
- automation [Office development in Visual Studio], Word
- host items [Office development in Visual Studio], Word
- automating Word
- controls [Office development in Visual Studio], Word host controls
- host controls, Word
- host controls [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], host controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 083fe8cdd3bf9d0e4de4809aacfb78b537e4ed8e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255541"
---
# <a name="automate-word-by-using-extended-objects"></a>확장 된 개체를 사용 하 여 Word 자동화
  Visual Studio에서 Word 솔루션을 개발하는 경우 솔루션에서 *호스트 항목* 및 *호스트 컨트롤*을 사용할 수 있습니다. Word 개체 모델, 즉 Word용 주 interop 어셈블리가 노출하는 개체 모델에서 일반적으로 사용되는 특정 개체(예: <xref:Microsoft.Office.Interop.Word.Document> 및 <xref:Microsoft.Office.Interop.Word.ContentControl> )를 확장하는 개체입니다. 확장된 개체는 기반이 되는 Word 개체처럼 동작하지만 개체에 이벤트 및 데이터 바인딩 기능을 더 추가합니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 사용할 수 있는 컨텍스트는 각 솔루션 형식마다 다를 수 있지만 호스트 항목과 호스트 컨트롤은 VSTO 추가 기능과 문서 수준 사용자 지정 둘 다에서 사용할 수 있습니다. 자세한 내용은 [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)를 참조 하세요.

## <a name="document-host-item"></a>문서 호스트 항목
 Word 프로젝트는 <xref:Microsoft.Office.Tools.Word.Document> 호스트 항목에 대한 액세스를 제공합니다. <xref:Microsoft.Office.Tools.Word.Document> 호스트 항목은 호스트 컨트롤 및 Windows Forms 컨트롤을 포함하여 다른 컨트롤에 대한 컨테이너 역할을 하고 해당 화면에 컨트롤에 대한 정보를 유지 관리합니다. 또한 <xref:Microsoft.Office.Tools.Word.Document> 호스트 항목은 Word의 개체 모델의 해당 클래스인 <xref:Microsoft.Office.Interop.Word.Document> 클래스와 대부분 동일한 구성원을 제공합니다.

 자세한 내용은 [문서 호스트 항목](../vsto/document-host-item.md)을 참조 하세요.

## <a name="word-host-controls"></a>Word 호스트 컨트롤
 문서를 만들고 구성 및 자동화하는 데 도움이 되는 여러 Word용 호스트 컨트롤이 있습니다. 대부분의 해당 기능은 데이터 가져오기, 표시 및 보호를 포함합니다. 이러한 호스트 컨트롤은 네이티브 Word 개체 모델의 해당 항목에 없는 이벤트 및 데이터 바인딩 기능을 제공합니다.

 문서 수준 프로젝트에서는 디자인 타임에 모든 호스트 컨트롤을 문서에 추가하거나 런타임에 콘텐츠 컨트롤과 책갈피 컨트롤을 추가할 수 있습니다. VSTO 추가 기능 프로젝트에서는 런타임에 열려 있는 임의 문서에 콘텐츠 컨트롤 및 책갈피 컨트롤을 추가할 수 있습니다.

 Word 프로젝트에서 사용할 수 있는 호스트 컨트롤에 대한 자세한 내용은 다음 항목을 참조하세요.

- [콘텐츠 컨트롤](../vsto/content-controls.md)

- [책갈피 컨트롤](../vsto/bookmark-control.md)

- [XMLNode 컨트롤](../vsto/xmlnode-control.md)

- [XMLNodes 컨트롤](../vsto/xmlnodes-control.md)

## <a name="see-also"></a>참고 항목
- [방법: Word 문서에 콘텐츠 컨트롤 추가](../vsto/how-to-add-content-controls-to-word-documents.md)
- [방법: Word 문서에 책갈피 컨트롤 추가](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [방법: Word 문서에 XMLNode 컨트롤 추가](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)
- [방법: Word 문서에 XMLNodes 컨트롤 추가](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [방법: 책갈피 컨트롤 크기 조정](../vsto/how-to-resize-bookmark-controls.md)
- [연습: 콘텐츠 컨트롤을 사용 하 여 템플릿 만들기](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)
- [연습: 콘텐츠 컨트롤을 사용자 지정 XML 부분에 바인딩](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)
- [연습: 책갈피에 대 한 바로 가기 메뉴 만들기](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Word 솔루션](../vsto/word-solutions.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍에 대 한 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [런타임에 VSTO 추가 기능에서 Word 문서 및 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

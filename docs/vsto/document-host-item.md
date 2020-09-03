---
title: 문서 호스트 항목
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- documents [Office development in Visual Studio], document host items
- document host items
- Word [Office development in Visual Studio], Word documents
- Word [Office development in Visual Studio]
- Word documents
- host items [Office development in Visual Studio], Document
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ebea0c3a09d08741523deddce94def170d844202
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71253703"
---
# <a name="document-host-item"></a>문서 호스트 항목
  <xref:Microsoft.Office.Tools.Word.Document> 호스트 항목은 Word용 주 interop 어셈블리의 <xref:Microsoft.Office.Interop.Word.Document> 형식을 확장한 형식입니다. <xref:Microsoft.Office.Tools.Word.Document> 호스트 항목은 <xref:Microsoft.Office.Interop.Word.Document> 개체와 동일한 모든 속성, 메서드 및 이벤트를 제공할 뿐 아니라 추가 이벤트를 노출하고 호스트 컨트롤 및 Windows Forms 컨트롤에 대한 컨테이너 역할을 합니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 문서 수준 프로젝트에는 프로젝트의 문서를 나타내는 기본 <xref:Microsoft.Office.Tools.Word.Document> 호스트 항목이 있습니다. VSTO 추가 기능 프로젝트에서 런타임에 <xref:Microsoft.Office.Tools.Word.Document> 호스트 항목을 생성할 수 있습니다.

## <a name="understand-the-document-host-item-in-document-level-projects"></a>문서 수준 프로젝트의 문서 호스트 항목 이해
 프로젝트의 문서에 액세스하려면 `ThisDocument` 클래스를 사용합니다. 문서 수준 프로젝트를 만들 때 Visual Studio는 `ThisDocument` 클래스를 생성하여 Word와 사용자 지정 코드 사이의 통신 링크로 사용합니다. `ThisDocument` 클래스는 <xref:Microsoft.Office.Tools.Word.Document> 호스트 항목의 멤버에 대한 액세스를 제공하여 문서를 열거나 닫을 때 코드를 실행하는 등 사용자 지정에서 기본 작업을 수행합니다. 또한 클래스를 사용하여 컨트롤을 문서에 추가할 수도 있습니다. 다양한 컨트롤 집합을 결합하고 코드를 작성하여 컨트롤을 데이터에 바인딩하고, 사용자로부터 정보를 수집하고, 사용자 작업에 응답할 수 있습니다. 자세한 내용은 [문서 수준 사용자 지정 프로그래밍](../vsto/programming-document-level-customizations.md)을 참조 하세요.

 `ThisDocument` 클래스는 프로젝트에서 코드를 작성하기 시작할 수 있는 위치를 제공합니다. 이 클래스는 Word용 주 interop 어셈블리의 <xref:Microsoft.Office.Interop.Word.Document> 개체와 동일한 모든 속성, 메서드 및 이벤트를 제공하므로 `ThisDocument` 을 사용하여 Word의 개체 모델에 액세스할 수도 있습니다. 자세한 내용은 [Word 개체 모델 개요](../vsto/word-object-model-overview.md)를 참조 하세요.

### <a name="limitations-of-the-document-host-item-in-document-level-projects"></a>문서 수준 프로젝트의 문서 호스트 항목에 대 한 제한 사항
 문서 수준의 프로젝트에는 하나의 <xref:Microsoft.Office.Tools.Word.Document> 호스트 항목(즉, `ThisDocument` 클래스)만 포함할 수 있습니다. 문서 수준 사용자 지정에서는 디자인 타임에 새 <xref:Microsoft.Office.Tools.Word.Document> 호스트 항목을 프로젝트에 추가할 수 없고 런타임에 새 <xref:Microsoft.Office.Tools.Word.Document> 호스트 항목을 만들 수 없습니다.

 런타임에 새 Word 문서를 만드는 경우 <xref:Microsoft.Office.Interop.Word.Document>형식이 됩니다. 이 형식은 호스트 항목이 아니므로 호스트 컨트롤 또는 Windows Forms 컨트롤을 포함할 수 없습니다. 런타임에 문서를 만드는 방법에 대 한 자세한 내용은 [방법: 프로그래밍 방식으로 새 문서 만들기](../vsto/how-to-programmatically-create-new-documents.md)를 참조 하세요.

## <a name="understand-document-host-items-in-application-level-projects"></a>응용 프로그램 수준 프로젝트의 문서 호스트 항목 이해
 VSTO 추가 기능 프로젝트에서는 런타임에 Word에서 열리는 문서에 대한 <xref:Microsoft.Office.Tools.Word.Document> 호스트 항목을 생성할 수 있습니다. <xref:Microsoft.Office.Tools.Word.Document> 호스트 항목을 사용하여 연결된 문서에 컨트롤을 추가하거나 <xref:Microsoft.Office.Interop.Word.Document> 개체에서 사용할 수 없는 이벤트를 처리할 수 있습니다.

 <xref:Microsoft.Office.Tools.Word.Document> 호스트 항목을 생성하려면 `GetVstoObject` 메서드를 사용합니다. 자세한 내용은 [런타임에 VSTO 추가 기능에서 Word 문서 및 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)을 참조 하세요.

## <a name="see-also"></a>추가 정보
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [확장 된 개체를 사용 하 여 Word 자동화](../vsto/automating-word-by-using-extended-objects.md)
- [Word 개체 모델 개요](../vsto/word-object-model-overview.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍에 대 한 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [런타임에 VSTO 추가 기능에서 Word 문서 및 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

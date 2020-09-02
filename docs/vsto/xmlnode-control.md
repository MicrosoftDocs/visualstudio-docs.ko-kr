---
title: XMLNode 컨트롤
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a8bd5c4612b59f909ae623eb4092a209798f98c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62975729"
---
# <a name="xmlnode-control"></a>XMLNode 컨트롤
  **중요** Microsoft word와 관련 하 여이 항목에서 설명 하는 정보는 microsoft word에서 사용자 지정 XML과 관련 된 특정 기능의 구현을 제거 했을 때 미국 및 해당 지역 외부에 있거나 microsoft에서 실행 되는 프로그램 (1 월 2010 이전에 Microsoft에서 사용이 허가 된 Microsoft Word 제품)의 혜택 및 사용을 위해서만 제공 됩니다. Microsoft Word에 대 한이 정보는 microsoft word 제품이 2010 년 1 월 10 일 이후 Microsoft에서 사용이 허가 된 Microsoft Word 제품,에서 실행 되는 프로그램을 개발 하거나 사용 하는 미국 또는 지역에 있는 개인 또는 조직에서 읽거나 사용할 수 없습니다. 이러한 제품은 해당 날짜 이전에 사용이 허가 된 제품과 동일 하 게 작동 하지 않습니다.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 <xref:Microsoft.Office.Tools.Word.XMLNode>컨트롤은 이벤트를 노출 하 고 데이터에 바인딩될 수 있는 매핑된 XML 노드 개체입니다. <xref:Microsoft.Office.Tools.Word.XMLNode>컨트롤은 반복 되지 않는 스키마 요소가 Microsoft Office Word 문서에 매핑될 때만 생성 됩니다. Visual Studio에서 XML 노드를 만든 후에는 Word 개체 모델을 트래버스 하지 않고 직접 프로그래밍할 수 있습니다.

 <xref:Microsoft.Office.Tools.Word.XMLNode>Word에서 요소 매핑을 제거 하 여 컨트롤을 삭제할 수 있습니다.

## <a name="bind-data-to-the-control"></a>컨트롤에 데이터 바인딩
 <xref:Microsoft.Office.Tools.Word.XMLNode>컨트롤은 단순 데이터 바인딩을 지원 합니다. XML 노드는 속성을 사용 하 여 데이터 소스에 바인딩되어야 합니다 <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> . 바인딩된 데이터 세트의 데이터가 업데이트되면 <xref:Microsoft.Office.Tools.Word.XMLNode> 컨트롤이 변경 내용을 반영합니다.

## <a name="formatting"></a>서식 지정
 개체에 적용할 수 있는 서식은 <xref:Microsoft.Office.Interop.Word.XMLNode> 컨트롤에 적용할 수 있습니다 <xref:Microsoft.Office.Tools.Word.XMLNode> . 여기에는 글꼴, 밑줄 스타일 및 문자 스타일이 포함 됩니다.

## <a name="events"></a>이벤트
 <xref:Microsoft.Office.Tools.Word.XMLNode> 컨트롤에 대해 다음 이벤트를 사용할 수 있습니다.

- <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>

## <a name="compare-events"></a>이벤트 비교
 사용자가 자신의 커서를 특정 컨트롤의 컨텍스트 안으로 이동할 때 이벤트를 캡처할 수 있습니다 <xref:Microsoft.Office.Tools.Word.XMLNode> . 예를 들어 라는 <xref:Microsoft.Office.Tools.Word.XMLNode> `Customer` 자식 컨트롤을 포함 하는 라는 컨트롤이 있고 <xref:Microsoft.Office.Tools.Word.XMLNode> `Company` `Company` 다음과 같이 라는 두 개의 자식 컨트롤이 있습니다 <xref:Microsoft.Office.Tools.Word.XMLNode> `CompanyName` `CompanyRegion` .

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 커서를 노드로 이동할 때마다 작업 창에 컨트롤을 표시 하려는 경우 `Company` 에는 커서가 `CompanyName` `CompanyRegion` 의 컨텍스트 내에 있는지 여부에 상관 없습니다 `Company` . 이 경우의 이벤트에서 코드를 작성할 수 있습니다 <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> `Company` .

 대부분의 경우 커서가 <xref:Microsoft.Office.Tools.Word.XMLNode> 컨트롤로 들어가면 <xref:Microsoft.Office.Tools.Word.XMLNode.Select> 및 <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> 이벤트가 모두 발생 합니다. 다음 표에서는 이러한 이벤트의 차이점을 보여 줍니다.

|이벤트 선택|ContextEnter 이벤트|
|------------------|------------------------|
|커서를 안에 배치할 때 발생 <xref:Microsoft.Office.Tools.Word.XMLNode> 합니다.|커서가 노드의 컨텍스트 바깥쪽 영역에서 <xref:Microsoft.Office.Tools.Word.XMLNode> 또는 하위 노드 중 하나에 배치되는 경우에 발생합니다. 즉, 컨텍스트가 변경 될 때만 발생 합니다.|

 예를 들어 커서를 외부에서로 이동 하는 경우, `Customer` `CompanyName` <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> 및에 대 한 이벤트가 `Customer` `Company` `CompanyName` 발생 합니다. 그런 다음 커서를에서로 이동 하는 경우 `CompanyName` `CompanyRegion` <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> 에 `CompanyRegion` 도 및의 컨텍스트 내에서에 대 한 이벤트만 발생 합니다 `Company` `Customer` .

 이벤트와 이벤트 간에는 동일한 차이점이 있습니다 <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> .

## <a name="see-also"></a>추가 정보
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [확장 된 개체를 사용 하 여 Word 자동화](../vsto/automating-word-by-using-extended-objects.md)
- [XMLNodes 컨트롤](../vsto/xmlnodes-control.md)
- [방법: Word 문서에 XMLNode 컨트롤 추가](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)
- [방법: Visual Studio 내부의 Word 문서에 스키마 매핑](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍에 대 한 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)

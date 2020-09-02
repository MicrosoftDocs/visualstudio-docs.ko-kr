---
title: XML 스키마 탐색기에서 작업 영역에 노드 추가
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 751e291188e6357343936d61d56f07bd86f97eaf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816399"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>방법: XML 스키마 탐색기에서 작업 영역에 노드 추가

이 항목에서는 **XML 스키마 탐색기**에서 [XML 스키마 디자이너 작업 영역](../xml-tools/xml-schema-designer-workspace.md)에 노드를 추가하는 방법에 대해 설명합니다. 이렇게 노드를 추가하려면 **XML 스키마 탐색기**에서 XSD 디자이너 뷰로 노드를 끌어다 놓거나 **XML 스키마 탐색기**의 상황에 맞는 메뉴를 사용해야 합니다. 또한 **XML 스키마 탐색기**에서 수행된 검색 결과로 강조 표시된 노드를 추가할 수 있습니다. 자세한 내용은 [방법: 작업 영역에 스키마 집합 검색 결과 노드 추가](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md)

> [!NOTE]
> 전역 노드만 [XML 스키마 디자이너 작업 영역](../xml-tools/xml-schema-designer-workspace.md)에 추가할 수 있습니다.

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>XML 탐색기의 상황에 맞는 메뉴를 통해 노드를 추가하는 방법

1. [:방법 XSD 스키마 파일 만들기 및 편집](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)의 단계를 수행합니다.

2. XSD 탐색기에서 `PurchaseOrderType` 노드를 마우스 오른쪽 단추로 클릭합니다. **그래프 뷰로 표시**를 선택합니다.

     그래프 뷰의 디자인 화면에 `purchaseOrderType` 노드가 나타납니다.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>노드를 뷰로 끌어서 놓는 방법

1. 그래프 뷰에서 `PurchaseOrderType` 노드를 마우스 오른쪽 단추로 클릭합니다. **XML 스키마 탐색기에 표시**를 선택합니다.

     **XML 스키마 탐색기**에서 노드가 강조 표시됩니다.

2. **XML 스키마 탐색기**에서 `PurchaseOrderType` 노드를 마우스 오른쪽 단추로 클릭하고 **모든 참조 표시**를 선택합니다.

     `purchaseOrder` 노드가 강조 표시됩니다.

3. `purchaseOrder` 노드를 그래픽 뷰로 끕니다.

     `purchaseOrder` 노드 및 `PurchaseOrderType` 노드가 그래프 뷰의 디자인 화면에 나란히 나타납니다. 이 두 노드는 서로 관련되어 있으므로(`purchaseOrder` 요소가 `PurchaseOrderType` 형식임) 두 노드 사이에 화살표가 그려집니다.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>스키마 탐색기 검색 기능을 사용하여 노드를 추가하는 방법

1. [XML 탐색기](../xml-tools/xml-schema-explorer.md) 도구 모음의 검색 텍스트 상자에 “purchaseOrder”를 입력하고 검색 단추를 클릭합니다.

     ![XML 스키마 탐색기 키워드 검색](../xml-tools/media/schemaexplorersearch.gif)

     또한 검색 결과가 **XML 스키마 탐색기**에서 강조 표시되고 세로 스크롤 막대의 눈금 표시로 나타납니다.

2. 요약 결과 창에서 **작업 영역에 선택한 노드 추가** 단추를 클릭하여 작업 영역에 검색 결과를 추가합니다.

     ![XML 스키마 탐색기 검색 결과](../xml-tools/media/schemaexplorersearchresult.gif)

     `purchaseOrder` 노드 및 `PurchaseOrderType` 노드가 [그래프 뷰](../xml-tools/graph-view.md)의 디자인 화면에 나란히 나타납니다. 이 두 노드는 서로 관련되어 있으므로(`purchaseOrder` 요소가 `PurchaseOrderType` 형식임) 두 노드 사이에 화살표가 그려집니다.

## <a name="see-also"></a>참조

- [XML 스키마 탐색기](../xml-tools/xml-schema-explorer.md)

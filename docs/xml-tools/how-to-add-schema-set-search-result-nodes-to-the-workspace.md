---
title: 작업 영역에 XML 스키마 집합 검색 결과 노드 추가
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d94544fd017809b32b7a144b16da4515e6b2e4bb
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816321"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>방법: 작업 영역에 스키마 집합 검색 결과 노드 추가

이 항목에서는 작업 영역에서 키워드 검색을 수행한 결과로 **XML 스키마 탐색기**에서 강조 표시되는 노드를 추가하는 방법에 대해 설명합니다.

> [!NOTE]
> 전역 노드만 [작업 영역](../xml-tools/xml-schema-designer-workspace.md)에 추가할 수 있습니다.

이 예제에서는 샘플 [구매 주문 스키마](../xml-tools/sample-xsd-file-purchase-order-schema.md)를 사용합니다.

## <a name="to-add-schema-set-result-nodes"></a>스키마 집합 결과 노드를 추가하려면

1. [:방법 XSD 스키마 파일 만들기 및 편집](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)의 단계를 수행합니다.

2. [XML 탐색기](../xml-tools/xml-schema-explorer.md) 도구 모음의 검색 텍스트 상자에 “purchaseOrder”를 입력하고 검색 단추를 클릭합니다.

     ![XML 스키마 탐색기 키워드 검색](../xml-tools/media/schemaexplorersearch.gif)

     또한 검색 결과가 **XML 스키마 탐색기**에서 강조 표시되고 세로 스크롤 막대의 눈금 표시로 나타납니다.

3. 요약 결과 창에서 **작업 영역에 선택한 노드 추가** 단추를 클릭하여 작업 영역에 검색 결과를 추가합니다.

     ![XML 스키마 탐색기 검색 결과](../xml-tools/media/schemaexplorersearchresult.gif)

     `purchaseOrder` 노드 및 `PurchaseOrderType` 노드가 [그래프 뷰](../xml-tools/graph-view.md)의 디자인 화면에 나란히 나타납니다. 이 두 노드는 서로 관련되어 있으므로(`purchaseOrder` 요소가 `PurchaseOrderType` 형식임) 두 노드 사이에 화살표가 그려집니다.

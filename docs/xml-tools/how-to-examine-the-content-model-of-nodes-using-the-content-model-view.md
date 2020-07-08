---
title: XML 스키마 디자이너에서 콘텐츠 모델 뷰를 사용하여 노드 검사
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81bf6294aeac9a23168bf9cf9aaec26efbfc6c1f
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815983"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>방법: 콘텐츠 모델 뷰를 사용하여 노드의 콘텐츠 모델 검사

이 항목에서는 [콘텐츠 모델 뷰](../xml-tools/content-model-view.md)를 사용하여 노드를 탐색하는 방법에 대해 설명합니다.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>콘텐츠 모델 뷰에서 새 XSD 파일을 만들고 루트 요소를 표시하려면

1. 새 XML 스키마 파일을 만듭니다.

2. 시작 뷰에서 **XML 편집기를 사용하여 기본 XML 스키마 파일 표시 및 편집**을 클릭합니다.

3. [샘플 XML 스키마: 구매 주문 스키마](../xml-tools/sample-xsd-file-purchase-order-schema.md)에서 XML 스키마 샘플 코드를 복사하고 붙여넣어 기본적으로 새 XSD 파일에 추가된 코드를 바꿉니다.

4. XML 편집기에서 `purchaseOrder` 요소를 마우스 오른쪽 단추로 클릭하고 **XML 탐색기에 표시**를 선택하여 스키마 탐색기에서 `purchaseOrder` 요소를 선택합니다.

5. XML 탐색기에서 `purchaseOrder`를 마우스 오른쪽 단추로 클릭하고 **콘텐츠 모델 뷰로 표시**를 선택합니다.

     콘텐츠 모델 뷰는 해당 디자인 화면에 `purchaseOrder` 요소를 표시합니다.

6. 각 노드를 두 번 클릭하거나 각 노드 오른쪽에 있는 양방향 화살표를 클릭하여 `shipTo`, `billTo` 및 `items` 노드를 확장합니다.

     이제 `purchaseOrder` 요소의 노드가 확장되고 요소의 콘텐츠 모델을 볼 수 있습니다.

7. `purchaseOrder` 요소 아래의 노드를 클릭하고 이동 경로 탐색 막대를 확인하여 스키마 집합에서 선택한 노드가 위치한 곳을 봅니다.

8. XSD 도구 모음에서 **설명서 표시** 단추를 클릭하여 설명서를 표시하거나 숨깁니다. 또한 디자인 화면을 마우스 오른쪽 단추로 클릭하여 설명서를 표시하거나 숨길 수 있습니다.

9. `purchaseOrder` 노드를 마우스 오른쪽 단추로 클릭하고 **샘플 XML 생성**을 선택하여 XML 인스턴스 문서를 봅니다.

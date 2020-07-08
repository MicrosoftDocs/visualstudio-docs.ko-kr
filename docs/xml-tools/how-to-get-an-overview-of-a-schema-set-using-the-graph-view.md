---
title: 'XML 스키마 디자이너: 그래프 뷰를 사용하여 스키마 집합 개요 가져오기'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50813b37bf8f0fa7b3a8dbbb8fd38c101f6bbadf
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817153"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>방법: 그래프 뷰를 사용하여 스키마 집합의 개요 가져오기

이 항목에서는 [그래프 뷰](../xml-tools/graph-view.md)를 사용하여 스키마 집합의 노드 및 이러한 노드 간 관계를 간략하게 설명합니다.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>콘텐츠 모델 뷰에서 새 XSD 파일을 만들고 루트 요소를 표시하려면

1. 새 XML 스키마 파일을 만들고 파일을 *Relationships.xsd*로 저장합니다.

2. 시작 뷰에서 **XML 편집기를 사용하여 기본 XML 스키마 파일 표시 및 편집** 링크를 클릭합니다.

3. [샘플 XML 스키마: 관계](../xml-tools/sample-xsd-file-relationships.md)에서 XML 스키마 샘플 코드를 복사하고 붙여넣어 기본적으로 새 XSD 파일에 추가된 코드를 바꿉니다.

4. XML 편집기의 아무 곳이나 마우스 오른쪽으로 클릭하고 **뷰 디자이너**를 선택합니다.

5. **XSD 도구 모음**에서 그래프 뷰를 선택합니다.

6. **XML 스키마 탐색기**에서 **스키마 집합** 노드를 선택하고 해당 노드를 그래프 뷰의 디자인 화면으로 끕니다. 모든 전역 노드 및 관계가 설정된 노드를 연결하는 화살표를 볼 수 있어야 합니다.

     ![그래프 뷰](../xml-tools/media/relationshipingraphview.gif)

7. 디자인 화면의 노드를 클릭하고 이동 경로 탐색 막대를 확인하여 스키마 집합에서 선택한 노드가 위치한 곳을 봅니다.

8. 디자인 화면의 요소 노드를 마우스 오른쪽 단추로 클릭하고 **샘플 XML 생성**을 선택하여 XML 인스턴스 문서를 봅니다.

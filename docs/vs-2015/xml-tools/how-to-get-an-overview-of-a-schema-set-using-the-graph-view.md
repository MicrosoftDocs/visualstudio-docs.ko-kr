---
title: '방법: 그래프 뷰를 사용 하 여 스키마 집합의 개요 가져오기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7009e5772b4f4c6977d58d2c52d733999a0d9369
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670890"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>방법: 그래프 뷰를 사용하여 스키마 집합의 개요 가져오기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 [그래프 뷰](../xml-tools/graph-view.md)를 사용하여 스키마 집합의 노드 및 이러한 노드 간 관계를 간략하게 설명합니다.

### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>콘텐츠 모델 뷰에서 새 XSD 파일을 만들고 루트 요소를 표시하려면

1. 새 XML 스키마 파일을 만들고 파일을 Relationships.xsd로 저장합니다.

2. **Xml 편집기를 사용 하 여 시작 뷰에서 기본 Xml 스키마 파일 보기 및 편집을** 클릭 합니다.

3. [샘플 Xml 스키마: 관계](../xml-tools/sample-xsd-file-relationships.md) 에서 xml 스키마 샘플 코드를 복사 하 고 붙여 넣어 기본적으로 새 XSD 파일에 추가 된 코드를 바꿉니다.

4. XML 편집기의 아무 곳 이나 마우스 오른쪽 단추로 클릭 하 고 **디자이너 보기**를 선택 합니다.

5. XSD 도구 모음에서 그래프 뷰를 선택합니다.

6. XML 스키마 탐색기에서 **스키마 집합** 노드를 선택 하 고 노드를 그래프 뷰의 디자인 표면으로 끕니다. 모든 전역 노드 및 관계가 설정된 노드를 연결하는 화살표를 볼 수 있어야 합니다.

     ![그래프 뷰](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")

7. 디자인 화면의 노드를 클릭하고 이동 경로 탐색 막대를 확인하여 스키마 집합에서 선택한 노드가 위치한 곳을 봅니다.

8. Rick에서 요소 노드를 클릭 하 고 **샘플 Xml 생성** 을 선택 하 여 xml 인스턴스 문서를 표시 합니다.

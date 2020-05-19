---
title: XML 스키마 디자이너 작업 영역
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 588fa495-fe7f-4b16-8a9f-6b6b8d2d502a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4cf86dd39e010424b25916deec8cdebd23ee1c1b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592375"
---
# <a name="xml-schema-designer-workspace-views"></a>XML 스키마 디자이너 작업 영역 뷰

XML 스키마 디자이너(XSD 디자이너)는 XML 스키마를 탐색하는 데 사용되는 그래픽 도구입니다. XSD 디자이너에서는 XML 스키마 트리를 탐색 및 찾아보고 검색을 수행할 수 있는 [XML 스키마 탐색기](../xml-tools/xml-schema-explorer.md) 이외에도 XSD 스키마를 보다 자세히 탐색할 수 있는 세 가지 뷰를 제공합니다.

- **시작 뷰**는 XSD 디자이너의 시작 지점입니다. 시작 뷰에서 XSD 디자이너의 다른 뷰로 탐색하고 스키마 집합의 세부 정보를 확인할 수 있습니다.
- **그래프 뷰**를 통해 스키마 집합 및 스키마 노드 간 관계를 간략하게 볼 수 있습니다.
- **콘텐츠 모델 뷰**에서는 단순/복합 형식, 요소, 그룹, 특성 및 특성 그룹을 포함하여 로컬 스키마 노드와 전역 스키마 노드의 세부 정보를 그래픽으로 표현할 수 있습니다.

관심 있는 노드 탐색을 시작하려면 해당 노드를 작업 영역에 추가해야 합니다. 작업 영역은 모든 뷰 간에 공유됩니다.

## <a name="add-nodes-to-the-workspace"></a>작업 영역에 노드 추가

다음 방법으로 작업 영역에 노드를 추가할 수 있습니다.

- [시작 뷰](../xml-tools/start-view.md)의 “스키마 집합 정보” 섹션에서 전역 노드 형식 옆에 있는 **추가** 링크를 클릭합니다.

- 전역 노드, 파일 노드 및 네임스페이스 노드를 **XML 스키마 탐색기**에서 세 개의 뷰로 끌어서 놓습니다. 자세한 내용은 [XML 스키마 탐색기](../xml-tools/xml-schema-explorer.md)의 “노드 끌어서 놓기” 섹션을 참조하세요.

- **XML 스키마 탐색기**에서 상황에 맞는(오른쪽 클릭) 메뉴를 사용합니다. 자세한 내용은 [상황에 맞는 메뉴](../xml-tools/context-menus-xml-schema-explorer.md)를 참조하세요.

- XSD 탐색기에서 검색 작업을 수행하고 요약 결과 창에서 **작업 영역에 선택한 노드 추가** 단추를 클릭합니다. 자세한 내용은 [스키마 집합 검색](../xml-tools/searching-the-schema-set.md)을 참조하세요.

## <a name="switch-views"></a>뷰 전환

뷰를 전환하려면 다음 중 하나를 사용합니다.

- XSD 디자이너 도구 모음

- 콘텐츠 모델 뷰 및 그래프 뷰의 상황에 맞는(오른쪽 클릭) 메뉴

- 시작 뷰 페이지의 워터마크, 빈 콘텐츠 모델 뷰 또는 그래프 뷰의 워터마크

- 바로 가기 키: 시작 뷰의 경우 **Ctrl**+**1**, 그래프 뷰의 경우 **Ctrl**+**2**, 콘텐츠 모델 뷰의 경우 **Ctrl**+**3**

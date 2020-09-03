---
title: 정렬, 필터링 및 그룹화 (XML 스키마 탐색기) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99c28842a92ab598ff196e80fc96678c256e4db8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656143"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>정렬, 필터링 및 그룹화(XML 스키마 탐색기)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 **XML 스키마 탐색기** 도구 모음의 정렬, 필터링 및 그룹화 옵션 메뉴에서 사용할 수 있는 옵션에 대해 설명합니다.

## <a name="filter-options"></a>필터 옵션
 사용할 수 있는 필터 옵션은 다음과 같습니다. 기본적으로 **네임스페이스 표시** 및 **스키마 파일 표시** 옵션이 선택되어 있습니다.

- **네임스페이스 표시**

- **스키마 파일 표시**

- **식자공 표시(시퀀스/선택/모두)**

## <a name="sorting-options"></a>정렬 옵션
 사용할 수 있는 정렬 옵션은 다음과 같습니다. 기본값은 **유형별 정렬**입니다. 정렬 기준 옵션은 파일 및 네임스페이스에 적용되지 않습니다.

- **유형별 정렬**

- **이름순 정렬**

- **문서 순서**

### <a name="sort-by-type"></a>유형별 정렬
 **유형별 정렬** 옵션을 선택하면 전역 노드가 다음 순서로 정렬됩니다. 그런 다음 노드가 각 그룹 내에서 알파벳순으로 정렬됩니다.

1. `import` 노드

2. `include` 노드

3. `redefine` 노드

4. `attribute` 노드

5. `attributeGroup` 노드

6. `complexType` 노드

7. `simpleType` 노드

8. `element` 노드

9. `group` 노드

### <a name="sort-by-name"></a>이름순 정렬
 **이름순 정렬** 옵션을 선택하면 전역 노드가 다음 순서로 정렬됩니다.

1. `import` 노드(네임스페이스의 알파벳 순서로 정렬)

2. `include` 노드(`schemaLocation` 특성의 알파벳 순서로 정렬)

3. `redefine` 노드(`schemaLocation` 특성의 알파벳 순서로 정렬)

4. 기타 전역 노드(알파벳 순서로 정렬)

### <a name="document-order"></a>문서 순서
 **문서 순서** 옵션은 **스키마 파일 표시** 옵션을 선택한 경우 사용할 수 있습니다. **문서 순서**를 선택하면 전역 노드가 스키마 파일에 표시된 순서대로 표시됩니다.

## <a name="persisting-sortfilter-options"></a>정렬/필터 옵션 유지
 설정이 변경될 때 솔루션 또는 파일이 열려 있는지 여부에 상관없이 정렬, 필터링 및 그룹화 옵션이 각 사용자에 대한 레지스트리에 저장됩니다.

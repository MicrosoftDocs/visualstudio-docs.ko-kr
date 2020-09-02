---
title: 전체 텍스트 검색 팁 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- hv_search
helpviewer_keywords:
- Help Viewer 2.0, full-text search tips
- full-text search tips [Help Viewer 2.0]
ms.assetid: bcaad23d-2ca7-4bec-8b54-b884bc34e70b
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac683ff6e7079478d5b4e642918df4e281a53f0b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645648"
---
# <a name="full-text-search-tips"></a>전체 텍스트 검색 팁
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

도움말에서 정보를 찾는 유용한 방법 중 하나는 전체 텍스트 검색을 수행하는 것입니다. 결과를 구체화하고 사용자 지정하려면 구문이 쿼리에 미치는 영향을 이해해야 합니다. 이 항목에서는 쿼리 작성에 도움이 되는 팁, 절차 및 자세한 구문 정보를 제공합니다.

## <a name="full-text-search-tips"></a>전체 텍스트 검색 팁
 도움말에서 쿼리 형식을 해석하는 방법을 알고 있으면 관련된 항목만 반환하는 대상 지정 검색을 만들 수 있습니다. 이러한 형식에는 특수 문자, 예약어 및 필터가 포함됩니다.

### <a name="general-guidelines"></a>일반 지침
 다음 표에는 도움말의 검색 쿼리를 작성하기 위한 몇 가지 기본 규칙과 지침이 나와 있습니다.

|구문|Description|
|------------|-----------------|
|대/소문자 구분|검색 시 대/소문자를 구분하지 않습니다. 대문자 또는 소문자를 사용하여 검색 조건을 작성합니다. 예를 들어 "OLE"와 "ole"는 동일한 결과를 반환합니다.|
|문자 조합|개별 문자(a–z) 또는 숫자(0-9)만 검색할 수는 없습니다. 특정 예약어(예: "and", "from" 및 "with")를 검색하려고 하면 무시됩니다. 자세한 내용은 이 항목의 뒷부분에 나오는 “검색에서 무시되는 단어(중지 단어)”를 참조하세요.|
|평가 순서|검색 쿼리는 왼쪽에서 오른쪽으로 평가됩니다.|

### <a name="search-syntax"></a>검색 구문
 여러 단어를 포함하는 검색 문자열(예: "word1 word2")을 지정하는 경우 해당 문자열은 "word1 AND word2"를 입력하는 것과 같으며, 검색 문자열의 개별 단어를 모두 포함하는 항목만 반환됩니다.

> [!IMPORTANT]
> 1. 문구 검색은 지원되지 않습니다. 검색 문자열에 여러 단어를 지정하는 경우 지정한 단어를 모두 포함하지만 지정한 정확한 문구가 아닌 항목도 반환됩니다.
>    2. 검색 문구에서 단어 간의 관계를 지정하려면 논리 연산자를 사용합니다. AND, OR, NOT, NEAR 등의 논리 연산자를 포함하여 검색을 구체화할 수 있습니다. 예를 들어 "declaring NEAR union"을 검색하는 경우 "declaring" 및 "union" 단어를 포함하고 그 사이에 몇 단어만 있는 항목이 검색 결과에 포함됩니다. 자세한 내용은 [검색 식의 논리 연산자](../ide/logical-operators-in-search-expressions.md)를 참조하세요.

### <a name="filters"></a>필터
 고급 검색 연산자를 사용하여 검색 결과를 더욱 제한할 수 있습니다. 도움말에는 전체 텍스트 검색 결과를 필터링하는 데 사용할 수 있는 세 가지 범주(제목, 코드 및 키워드)가 포함되어 있습니다. 자세한 내용은 [검색 식의 고급 검색 연산자](../ide/advanced-search-operators-in-search-expressions.md)를 참조하세요.

### <a name="ranking-of-search-results"></a>검색 결과의 순위 지정
 검색 알고리즘은 특정 조건을 적용하여 결과 목록에서 검색 결과의 순위를 위나 아래로 조정합니다. 일반적으로:

1. 제목에 검색어를 포함하는 콘텐츠의 순위가 그렇지 않은 콘텐츠보다 높습니다.

2. 근접한 위치에 검색어를 포함하는 콘텐츠의 순위가 그렇지 않은 콘텐츠보다 높습니다.

3. 높은 밀도의 검색어를 포함하는 콘텐츠의 순위가 낮은 밀도의 검색어를 포함하는 콘텐츠보다 높습니다.

### <a name="words-ignored-in-searches-stop-words"></a>검색에서 무시되는 단어(중지 단어)
 자주 사용되는 단어 또는 숫자(중지 단어라고도 함)는 전체 텍스트 검색 시 자동으로 무시됩니다. 예를 들어 "pass through" 문구를 검색하는 경우 검색 결과에 "pass" 단어를 포함하는 항목이 표시되지만 "through" 단어를 포함하는 항목은 표시되지 않습니다.

## <a name="see-also"></a>관련 항목
 [Locate Information](../ide/locate-information.md) [검색 식에서 정보 논리 연산자](../ide/logical-operators-in-search-expressions.md) 찾기

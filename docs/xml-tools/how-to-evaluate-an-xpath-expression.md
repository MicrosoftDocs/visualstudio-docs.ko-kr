---
title: 디버그하는 동안 XPath 식 계산
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2e0b6c84fa9447dc38aa7976fa59bb5aa67d5c3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592726"
---
# <a name="evaluate-xpath-expressions"></a>XPath 식 계산

디버그하는 동안 **간략한 조사식** 창을 사용하여 XPath 식을 계산할 수 있습니다. XPath 식은 W3C XPath 1.0 권장 사항에 따라 유효한 식이어야 합니다. 현재 XSLT 컨텍스트, 즉 **지역** 창의 `self::node()` 노드에서는 XPath 식에 대한 계산 컨텍스트를 제공합니다.

XPath 식을 계산할 때:

- 기본 제공 XPath 함수가 지원됩니다.

- 기본 제공 XSLT 함수 및 사용자 정의 함수는 지원되지 않습니다.

> [!NOTE]
> XSLT 디버깅은 Visual Studio의 Enterprise Edition에서만 사용할 수 있습니다.

## <a name="evaluate-an-xpath-expression"></a>XPath 식 계산

다음 절차에서는 [연습: XSLT 스타일시트 디버그](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md#sample-files) 페이지의 *below-average.xsl* 및 *books.xml* 파일을 사용합니다.

1. `xsl:if` 시작 태그에 중단점을 삽입합니다.

2. 디버깅을 시작하려면 메뉴 모음에서 **XML** > **XSLT 디버깅 시작**을 선택하거나 **Alt**+**F5**를 누릅니다.

   디버거가 시작되고 `xsl:if` 태그에서 중단됩니다.

3. 마우스 오른쪽 단추를 클릭하고 **간략한 조사식**을 선택합니다.

   **간략한 조사식** 창이 열립니다.

4. **간략한 조사식** 대화 상자의 **식** 필드에 `./price/text()`를 입력하고 **다시 계산**을 선택합니다.

   현재 book 노드의 가격이 **값** 상자에 나타납니다.

   ![간략한 조사식 창에서 XPath 식 계산](media/quickwatch-price.png)

5. XPath 식을 `./price/text() < $bookAverage`로 변경하고 **다시 계산**을 클릭합니다.

   **값** 상자에 XPath 식이 `true`로 계산되었음이 나타납니다.

## <a name="see-also"></a>참조

- [XSLT 디버그](../xml-tools/debugging-xslt.md)

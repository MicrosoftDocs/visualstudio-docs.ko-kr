---
title: 디버그 XSLT 스타일 시트
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd5882cc606bf241a281940464ba028e77986807
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79300944"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>연습: XSLT 스타일 시트 디버그

이 연습 단계에서는 XSLT 디버거를 사용하는 방법을 보여 줍니다. 이 단계에는 변수 보기, 중단점 설정 및 단계별로 코드 실행이 포함됩니다. 디버거를 사용하면 한 번에 한 줄의 코드를 실행할 수 있습니다.

이 연습에 대 한 준비, 먼저 로컬 컴퓨터에 두 [샘플 파일을](#sample-files) 복사 합니다. 하나는 스타일 시트이고, 하나는 스타일 시트에 대한 입력으로 사용할 XML 파일입니다. 이 연습에서 사용하는 스타일 시트는 비용이 평균 도서 가격보다 낮은 모든 책을 찾습니다.

> [!NOTE]
> XSLT 디버거는 비주얼 스튜디오의 엔터프라이즈 버전에서만 사용할 수 있습니다.

## <a name="start-debugging"></a>디버그 시작

1. **파일** 메뉴에서**파일** **열기를** > 선택합니다.

2. 평균 *이하의 파일을* 찾아 **열기를**선택합니다.

   스타일 시트는 XML 편집기에서 열립니다.

3. 문서 속성 창의 **입력** 필드에서 찾아보기**단추(...)를**클릭합니다. 속성 **창이** 표시되지 않으면 편집기의 열린 파일에서 아무 곳이나 마우스 오른쪽 단추로 클릭한 다음 **Properties를**선택합니다.

4. *books.xml* 파일을 찾은 다음 **열기를**선택합니다.

   이렇게 하면 XSLT 변환에 사용되는 원본 문서 파일이 설정됩니다.

5. 평균 이하의 12줄에 [중단점을](../debugger/using-breakpoints.md) *설정합니다.* 여러 가지 방법 중 하나로 이 작업을 수행할 수 있습니다.

   - 12줄에 있는 편집기여백을 클릭합니다.

   - 12줄의 아무 곳이나 클릭한 다음 **F9을**누릅니다.

   - 시작 태그를 마우스 오른쪽 단추로 클릭한 다음 **중단점** > **삽입 중단점을**선택합니다. `xsl:if`

      ![비주얼 스튜디오에서 XSL 파일에 중단점을 삽입합니다.](media/insert-breakpoint.PNG)

6. 메뉴 모음에서 **XML** > **시작 XSLT 디버깅을 선택합니다(또는** **Alt**+**F5**를 누릅니다).

   디버깅 프로세스가 시작됩니다.

   편집기에서 디버거는 스타일 시트의 `xsl:if` 요소에 배치됩니다. *평균 이하의* 다른 파일은 편집기에서 열립니다. 입력 파일 *books.xml의* 각 노드가 처리될 때 채워질 출력 파일입니다.

   **[보기]**- 이전 작업지 **,** 1도의 **창이** Visual Studio 창 아래쪽에 나타납니다. **지역 변수와** 현재 값을 모두 표시합니다. 여기에는 스타일시트에 정의된 변수가 포함되며 디버거에서 현재 컨텍스트에 있는 노드를 추적하는 데 사용하는 변수도 포함됩니다.

## <a name="watch-window"></a>조사식 창

입력 파일이 처리될 때 해당 값을 검사할 수 있도록 **Watch 1** 창에 두 개의 변수를 추가합니다. 로컬 **창을** 사용하여 보고싶은 변수가 이미 있는 경우 값을 검사할 수도 있습니다.

1. **디버그** 메뉴에서 **Windows** > **Watch** > **1을**선택합니다.

   **Watch 1** 창이 표시됩니다.

2. 이름 `$bookAverage` 필드를 **Name** 입력한 다음 **Enter**를 누릅니다.

   변수의 `$bookAverage` 값은 **값** 필드에 표시됩니다.

3. 다음 줄에 `self::node()` **이름** 필드를 입력한 다음 **Enter**를 누릅니다.

   `self::node()`는 현재 컨텍스트 노드로 계산되는 XPath 식입니다. `self::node()` XPath 식의 값은 첫 번째 book 노드입니다. 이 값은 변환을 진행하면서 변경됩니다.

4. 노드를 `self::node()` 확장한 다음 값이 있는 노드를 `price`확장합니다.

   ![비주얼 스튜디오에서 XSLT 디버깅 중 보기 창](media/xslt-debugging-watch-window.png)

   현재 책 노드의 책 가격 값을 보고 `$bookAverage` 이를 값과 비교할 수 있습니다. 책 가격이 평균보다 낮기 `xsl:if` 때문에 디버깅 프로세스를 계속할 때 조건이 성공해야 합니다.

## <a name="step-through-the-code"></a>코드를 단계별로 진행

1. 계속하려면 **F5를** 누릅니다.

   첫 번째 책 노드가 `xsl:if` 조건을 충족했기 때문에 책 노드가 평균 *이하의 출력* 파일에 추가됩니다. 디버거는 스타일시트의 `xsl:if` 요소에 다시 배치될 때까지 계속 실행됩니다. 이제 디버거가 *books.xml* 파일의 두 번째 책 노드에 배치됩니다.

   Watch **1** 창에서 `self::node()` 값이 두 번째 책 노드로 변경됩니다. 가격 요소 값을 검사하여 가격이 평균을 초과하는 것을 확인할 수 있으므로 `xsl:if` 조건은 실패해야 합니다.

2. 계속하려면 **F5를** 누릅니다.

   두 번째 책 노드가 `xsl:if` 조건을 충족하지 않으므로 책 노드가 *평균 이하의 출력* 파일에 추가되지 않습니다. 디버거는 스타일 시트의 `xsl:if` 요소에 다시 배치될 때까지 계속 실행됩니다. 이제 디버거가 *books.xml* `book` 파일의 세 번째 노드에 배치됩니다.

   Watch **1** 창에서 `self::node()` 값이 세 번째 책 노드로 변경됩니다. `price` 요소의 값을 검사하여 가격이 평균 보다 낮음이 있는지 확인할 수 있습니다. `xsl:if` 조건이 성공해야 합니다.

3. 계속하려면 **F5를** 누릅니다.

   `xsl:if` 조건이 충족되었기 때문에 세 번째 책이 *평균 이하의 출력* 파일에 추가됩니다. XML 문서에 있는 모든 book이 처리되었으므로 디버거가 중지됩니다.

## <a name="sample-files"></a>샘플 파일

다음 두 파일은 연습에 사용됩니다.

### <a name="below-averagexsl"></a>평균 이하.xsl

```xml
<?xml version='1.0'?>
<xsl:stylesheet version="1.0"
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="xml" encoding="utf-8"/>
  <xsl:template match="/">
    <xsl:variable name="bookCount" select="count(/bookstore/book)"/>
    <xsl:variable name="bookTotal" select="sum(/bookstore/book/price)"/>
    <xsl:variable name="bookAverage" select="$bookTotal div $bookCount"/>
    <books>
      <!--Books That Cost Below Average-->
      <xsl:for-each select="/bookstore/book">
        <xsl:if test="price &lt; $bookAverage">
          <xsl:copy-of select="."/>
        </xsl:if>
      </xsl:for-each>
    </books>
  </xsl:template>
</xsl:stylesheet>
```

### <a name="booksxml"></a>books.xml

```xml
<?xml version='1.0'?>
<!-- This file represents a fragment of a book store inventory database -->
<bookstore>
  <book genre="autobiography" publicationdate="1981" ISBN="1-861003-11-0">
    <title>The Autobiography of Benjamin Franklin</title>
    <author>
      <first-name>Benjamin</first-name>
      <last-name>Franklin</last-name>
    </author>
    <price>8.99</price>
  </book>
  <book genre="novel" publicationdate="1967" ISBN="0-201-63361-2">
    <title>The Confidence Man</title>
    <author>
      <first-name>Herman</first-name>
      <last-name>Melville</last-name>
    </author>
    <price>11.99</price>
  </book>
  <book genre="philosophy" publicationdate="1991" ISBN="1-861001-57-6">
    <title>The Gorgias</title>
    <author>
      <name>Plato</name>
    </author>
    <price>9.99</price>
  </book>
</bookstore>
```

## <a name="see-also"></a>참고 항목

- [XSLT 디버깅](../xml-tools/debugging-xslt.md)

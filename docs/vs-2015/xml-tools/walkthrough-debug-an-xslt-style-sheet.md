---
title: '연습: XSLT 스타일 시트 디버그 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2c205ff68ebc51d0b0f5b32038763c1741855d7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656114"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>연습: XSLT 스타일시트 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습 단계에서는 XSLT 디버거를 사용하는 방법을 보여 줍니다. 이 단계에는 변수 보기, 중단점 설정 및 단계별로 코드 실행이 포함됩니다. 스타일시트는 평균 책 가격보다 가격이 낮은 책을 모두 찾습니다.

### <a name="to-prepare-for-this-walkthrough"></a>이 연습을 준비하려면

1. 열려 있는 솔루션을 모두 닫습니다.

2. 두 샘플 파일을 로컬 컴퓨터에 복사합니다.

## <a name="start-debugging"></a>디버깅 시작

#### <a name="to-start-debugging"></a>디버깅을 시작하려면

1. **파일** 메뉴에서 **열기**를 가리킨 다음 **파일**을 클릭 합니다.

2. Belowavg.xsl 파일을 찾아 **열기**를 클릭 합니다.

    XML 편집기에서 스타일시트가 열립니다.

3. 문서 속성 창의 **입력** 필드에서 찾아보기 단추( **...** )를 클릭합니다

4. books.xml 파일을 찾고 **열기**를 클릭 합니다.

    그러면 XSLT 변형에 사용되는 소스 문서 파일이 설정됩니다.

5. 시작 태그를 마우스 오른쪽 단추로 클릭 하 고 `xsl:if` **중단점**을 가리킨 다음 **중단점 삽입**을 클릭 합니다.

6. XML 편집기 도구 모음에서 **XSL 디버깅** 단추를 클릭 합니다.

   그러면 디버깅 프로세스가 시작되고 디버거에서 사용하는 새 창 여러 개가 열립니다.

   입력 문서와 스타일시트가 표시되는 두 개의 창이 있습니다. 디버거는 이들 창을 사용하여 현재 실행 상태를 표시합니다. 디버거는 스타일시트의 `xsl:if` 요소와 books.xml 파일의 첫 번째 book 노드에 배치됩니다.

   지역 창에 모든 지역 변수 및 현재 값이 표시됩니다. 여기에는 스타일시트에 정의된 변수가 포함되며 디버거에서 현재 컨텍스트에 있는 노드를 추적하는 데 사용하는 변수도 포함됩니다.

   Xsl **출력** 창에 xsl 변환의 출력이 표시 됩니다. 이 창은 **Visual Studio 출력** 창과 별개입니다.

## <a name="watch-window"></a>조사식 창

#### <a name="to-use-the-watch-window"></a>조사식 창을 사용하려면

1. **디버그** 메뉴에서 **창**, **조사식**을 차례로 가리킨 다음 **조사식 1**을 클릭 합니다.

     그러면 조사식 1 창이 표시됩니다.

2. `$bookAverage` **이름** 필드에를 입력 하 고 enter 키를 누릅니다.

     `$bookAverage` 변수 값이 창에 표시됩니다.

3. `self::node()` **이름** 필드에를 입력 하 고 enter 키를 누릅니다.

     `self::node()`는 현재 컨텍스트 노드로 계산되는 XPath 식입니다. `self::node()` XPath 식의 값은 첫 번째 book 노드입니다. 이 값은 변환을 진행하면서 변경됩니다.

4. `self::node()` 노드를 확장한 다음 `price` 노드를 확장합니다.

     그러면 책 가격 값을 볼 수 있으며 `$bookAverage` 값과 쉽게 비교할 수 있습니다. 책 가격은 평균 아래이므로 `xsl:if` 조건은 성공해야 합니다.

## <a name="step-through-the-code"></a>단계별로 코드 실행
 디버거에서 한 번에 한 줄씩 코드를 실행할 수 있습니다.

#### <a name="to-step-through-the-code"></a>단계별로 코드를 실행하려면

1. 계속하려면 **F5** 키를 누릅니다.

     첫 번째 book 노드가 `xsl:if` 조건을 만족하기 때문에 book 노드가 XSL 출력 창에 추가됩니다. 디버거는 스타일시트의 `xsl:if` 요소에 다시 배치될 때까지 계속 실행됩니다. 이제 디버거가 books.xml 파일의 두 번째 book 노드에 배치됩니다.

     조사식 1 창에서 `self::node()` 값이 두 번째 book 노드로 변경됩니다. 가격 요소 값을 검사하여 가격이 평균을 초과하는 것을 확인할 수 있으므로 `xsl:if` 조건은 실패해야 합니다.

2. **F5**를 눌러 계속합니다.

     두 번째 book 노드는 `xsl:if` 조건을 충족하지 않으므로 이 XSL 출력 창에 추가되지 않습니다. 디버거는 스타일시트의 `xsl:if` 요소에 다시 배치될 때까지 계속 실행됩니다. 이제 디버거가 books.xml 파일의 세 번째 `book` 노드에 배치됩니다.

     조사식 1 창에서 `self::node()` 값이 세 번째 book 노드로 변경됩니다. `price` 요소의 값을 확인하면 가격이 평균보다 낮으므로 `xsl:if` 조건이 충족됨을 알 수 있습니다.

3. 계속하려면 **F5** 키를 누릅니다.

     `xsl:if` 조건을 만족했기 때문에 세 번째 book이 XSL 출력 창에 추가됩니다. XML 문서에 있는 모든 book이 처리되었으므로 디버거가 중지됩니다.

## <a name="sample-files"></a>샘플 파일
 다음 두 파일은 연습에 사용됩니다.

### <a name="belowavgxsl"></a>belowAvg.xsl

```
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
        <xsl:if test="price < $bookAverage">
          <xsl:copy-of select="."/>
        </xsl:if>
      </xsl:for-each>
    </books>
  </xsl:template>
</xsl:stylesheet>
```

### <a name="booksxml"></a>books.xml

```
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

## <a name="see-also"></a>관련 항목
 [XSLT 디버그](../xml-tools/debugging-xslt.md)

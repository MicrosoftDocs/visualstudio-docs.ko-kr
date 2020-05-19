---
title: '연습: XSLT 계층 구조 사용'
ms.date: 11/04/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 892c166504b9a33fdcbbe0af2605e8268a2b06e7
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592453"
---
# <a name="walkthrough-use-xslt-hierarchy"></a>연습: XSLT 계층 구조 사용

XSLT 계층 구조 도구를 사용하면 많은 XML 개발 작업을 간단하게 수행할 수 있습니다. XSLT 스타일시트에서는 `includes` 및 `imports` 명령을 사용하는 경우가 자주 있습니다. 컴파일은 주 스타일시트에서 시작하지만 XSLT 스타일시트를 컴파일했을 때 오류가 발생하는 경우 이러한 오류는 주 스타일시트와 다른 소스에서 발생된 것일 수 있습니다. 오류를 해결하거나 스타일시트를 편집하려면 포함되거나 가져온 스타일시트에 액세스할 수 있어야 합니다. 디버거에서 스타일시트를 단계별로 실행하면 포함되거나 가져온 스타일시트가 열릴 수 있으며 하나 이상의 포함된 스타일시트의 일부 지점에 중단점을 추가할 수 있습니다.

XSLT 계층 구조 도구가 유용한 다른 시나리오는 기본 제공 템플릿 규칙에 중단점을 지정하는 것입니다. 템플릿 규칙은 스타일시트의 각 노드에 대해 생성되며 노드와 일치하는 다른 템플릿이 없는 경우 `xsl:apply-templates`에 의해 호출되는 특수 템플릿입니다. 기본 제공 템플릿 규칙에서 디버깅을 구현하려면 XSLT 디버거가 임시 폴더에서 규칙을 사용하여 파일을 생성하고 주 스타일시트를 사용하여 이러한 파일을 함께 컴파일합니다. 일부 `xsl:apply-template`에서 코드를 한 단계씩 실행하지 않고는 주 스타일시트에 포함된 스타일시트를 찾거나 기본 제공 템플릿 규칙을 사용하여 스타일시트를 열기가 어려울 수 있습니다.

이 항목의 예제에서는 참조된 스타일시트에서의 디버깅을 보여 줍니다.

## <a name="to-debug-in-a-referenced-style-sheet"></a>참조된 스타일시트에서 디버그하는 방법

1. Visual Studio에서 XML 문서를 엽니다. 이 예제에서는 다음 문서를 사용합니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <?xml-stylesheet type="text/xsl" href="xslinclude.xsl"?>
    <COLLECTION>
      <BOOK>
        <TITLE>Lover Birds</TITLE>
        <AUTHOR>Cynthia Randall</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>The Sundered Grail</TITLE>
        <AUTHOR>Eva Corets</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>Splish Splash</TITLE>
        <AUTHOR>Paula Thurman</AUTHOR>
        <PUBLISHER>Scootney</PUBLISHER>
      </BOOK>
    </COLLECTION>
    ```

1. 다음 *xslincludefile.xsl*을 추가합니다.

    ```xml
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
          xml:space="preserve">

    <xsl:template match="TITLE">
       Title - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="AUTHOR">
       Author - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="PUBLISHER">
       Publisher - <xsl:value-of select="."/><BR/><!-- removed second <BR/> -->
    </xsl:template>

    </xsl:stylesheet>
    ```

3. 다음 *xslinclude.xsl* 파일을 추가합니다.

    ```xml
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

      <xsl:output method="xml" omit-xml-declaration="yes"/>

      <xsl:template match="/">
        <xsl:for-each select="COLLECTION/BOOK">
          <xsl:apply-templates select="TITLE"/>
          <xsl:apply-templates select="AUTHOR"/>
          <xsl:apply-templates select="PUBLISHER"/>
          <BR/>
          <!-- add this -->
        </xsl:for-each>
      </xsl:template>

      <!-- The following template rule will not be called,
      because the related template in the including stylesheet
      is called. If we move this template so that
      it follows the xsl:include instruction, this one
      will be called instead.-->
      <xsl:template match="TITLE">
        <DIV STYLE="color:blue">
          Title: <xsl:value-of select="."/>
        </DIV>
      </xsl:template>

      <xsl:include href="xslincludefile.xsl" />
    </xsl:stylesheet>
    ```

4. `<xsl:include href="xslincludefile.xsl" />` 명령에 중단점을 추가합니다.

5. 디버깅을 시작합니다.

6. `<xsl:include href="xslincludefile.xsl" />` 명령에서 디버거가 중지되면 **한 단계씩 코드 실행** 단추를 누릅니다. 참조된 스타일시트에서 디버깅을 계속할 수 있습니다. 계층 구조가 표시되며 디자이너에서 올바른 경로를 표시합니다.

## <a name="see-also"></a>참조

- [XSLT 프로파일러](../xml-tools/xslt-profiler.md)

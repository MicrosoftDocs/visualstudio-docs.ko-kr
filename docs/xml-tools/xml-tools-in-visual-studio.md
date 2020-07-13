---
title: XML 편집기 및 스키마 디자이너
ms.date: 11/04/2016
ms.topic: overview
f1_keywords:
- vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e763fa3475f26b9742ea5fb7061978e711eb22ea
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816425"
---
# <a name="overview-of-xml-tools-in-visual-studio"></a>Visual Studio의 XML 도구 개요

*XML(Extensible Markup Language)* 은 데이터를 설명하는 형식을 제공하는 생성 언어입니다. XML에서는 XSL(Extensible Stylesheet Language) 및 CSS(CSS 스타일시트)와 같은 연결된 스타일시트를 사용하여 데이터와 데이터 표시를 구분합니다. Visual Studio에 포함된 도구와 기능을 사용하면 보다 쉽게 XML, XSLT 및 XML 스키마에 대한 작업을 수행할 수 있습니다.

## <a name="xml-editor"></a>XML 편집기

[XML 편집기](xml-editor.md)는 XML 문서를 편집하는 데 사용됩니다. 이 편집기에서는 전체 XML 구문 검사 기능, 입력하는 동안의 스키마 유효성 검사 기능, 색 구분 표시 기능 및 IntelliSense를 제공합니다. 스키마 또는 문서 종류 정의를 지정한 경우 IntelliSense에서 이 스키마 또는 문서 종류 정의를 사용하여 허용되는 요소 및 특성을 나열합니다.

추가 기능은 다음과 같습니다.

- 스키마에 의해 생성된 코드 조각을 비롯한 XML 코드 조각 지원

- 요소를 확장 및 축소할 수 있도록 문서 개요 표시

- XSLT 변환을 실행하고 텍스트, XML 또는 HTML로 결과를 볼 수 있는 기능

- XML 인스턴스 문서에서 XSD(XML 스키마 정의 언어) 스키마를 생성하는 기능

- IntelliSense 지원을 포함하여 XSLT 스타일시트 편집 지원

- XML 스키마 탐색기

## <a name="xml-schema-designer"></a>XML 스키마 디자이너

[XML 스키마 디자이너](xml-schema-designer.md)는 XSD(XML 스키마 정의 언어) 스키마 작업을 수행할 수 있도록 Visual Studio 및 XML 편집기와 통합되었습니다.

## <a name="xslt-debugging"></a>XSLT 디버깅

Visual Studio에서 [XSLT 스타일시트를 디버그](../xml-tools/debugging-xslt.md)할 수 있습니다. 디버거를 사용하여 XSLT 스타일시트에 중단점을 설정하고 코드에서 XSLT 스타일시트를 한 단계씩 실행하는 등의 작업을 수행할 수 있습니다.

> [!NOTE]
> XSLT 디버거는 Visual Studio의 Enterprise Edition에서만 사용할 수 있습니다.

## <a name="see-also"></a>참조

- <xref:System.Xml?displayProperty=fullName>
- [XSLT 변환](/dotnet/standard/data/xml/xslt-transformations)
- [XPath 데이터 모델을 사용하여 XML 데이터 처리](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)
- [XML DOM(문서 개체 모델)](/dotnet/standard/data/xml/xml-document-object-model-dom)
- [XML SOM(스키마 개체 모델)](/dotnet/standard/data/xml/xml-schema-object-model-som)

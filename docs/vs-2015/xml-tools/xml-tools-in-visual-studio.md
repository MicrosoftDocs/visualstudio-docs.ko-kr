---
title: XML 도구
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
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
- XML [Visual Studio], .NET Framework classes
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
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b9a46523c4c856367e77c345c7e44d0dbc87508f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845979"
---
# <a name="xml-tools-in-visual-studio"></a>Visual Studio의 XML 도구
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML(Extensible Markup Language) (XML) *는 데이터를 설명 하는 형식을 제공 하는 태그 언어입니다. 이 언어를 사용하면 콘텐츠를 보다 정확하게 선언하고 여러 플랫폼 간에 보다 의미 있는 검색 결과를 얻을 수 있습니다. 또한 XML을 사용하는 경우 표시를 데이터 자체와 구분할 수 있습니다. 예를 들어 HTML에서는 태그를 사용하여 데이터를 굵게, 기울임꼴 등으로 표시하도록 브라우저에 명령하지만 XML에서는 태그를 사용하여 구/군/시 이름, 기온, 기압 등의 데이터만을 설명합니다. XML에서는 XSL(Extensible Stylesheet Language) 및 CSS(CSS 스타일시트)와 같은 스타일시트를 사용하여 브라우저에 데이터를 표시합니다. XML에서는 데이터가 표시 및 프로세스와 구분되므로 여러 스타일시트 및 애플리케이션을 적용하여 데이터를 원하는 방식으로 표시 및 처리할 수 있습니다.

 XML은 웹을 통해 제공하도록 최적화된 SGML의 하위 집합으로, W3C(World Wide Web Consortium)에 의해 정의되었습니다. 이러한 표준화로 인해 구조적 데이터가 애플리케이션이나 공급업체와 상관없이 일정하게 유지됩니다.

 XML은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 및 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]에서 제공되는 여러 기능의 핵심적 요소입니다. 다음 항목에서는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 및 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]에서 제공되는 XML 관련 기능 및 도구의 이름을 소개합니다.

 자세한 내용은 xml 개발자를 위한 최신 설명서, 기술 정보, 다운로드, 뉴스 그룹 및 기타 리소스를 제공 하는 [Xml 개발자 센터](https://msdn.microsoft.com/data/bb190600.aspx)를 참조 하십시오.

## <a name="in-this-section"></a>섹션 내용
 [XML 데이터 작업](../xml-tools/working-with-xml-data.md) 에서 데이터가 처리 되는 방식에 대 한 XML의 역할에 대해 설명 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 [XSLT 디버깅](../xml-tools/debugging-xslt.md) Visual Studio 디버거를 사용 하 여 XSLT를 디버그 하는 방법에 대 한 항목의 링크를 제공 합니다.

## <a name="reference"></a>참조
 [Microsoft.VisualStudio.Xml편집기](https://msdn.microsoft.com/library/microsoft.visualstudio.xmleditor.aspx)System.Xml를 통해 [XML 편집기](https://msdn.microsoft.com/library/ms255810.aspx) 구문 분석 트리를 노출 합니다 [ . ](https://msdn.microsoft.com/library/system.xml.linq.aspx) 모든 XML 문서용 Linq입니다.

 [XML 표준 참조](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) Xml, DTD (문서 종류 정의), XSD (XML 스키마 정의 언어) 및 XSLT를 비롯 한 XML 기술에 대 한 정보를 제공 합니다.

 <xref:System.Xml?displayProperty=fullName> 네임 스페이스를 구성 하는 클래스 및 기타 요소에 대해 설명 <xref:System.Xml> 하 고 각 항목에 대 한 자세한 정보에 대 한 링크를 제공 합니다.

 <xref:System.Xml.Serialization?displayProperty=fullName> 네임 스페이스를 구성 하는 클래스 및 기타 요소에 대해 설명 <xref:System.Xml.Serialization> 하 고 각 항목에 대 한 자세한 정보에 대 한 링크를 제공 합니다.

## <a name="related-sections"></a>관련 섹션
 [XML 문서 개체 모델 (DOM)](https://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) <xref:System.Xml.XmlDocument> 및 이와 관련 된 클래스가 W3C 문서 개체 모델 (코어) 수준 1 및 수준 2 네임 스페이스 지원 사양을 준수 하는 방법에 대해 설명 합니다.

 [XmlReader를 사용 하 여 XML 읽기](https://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) 에서 <xref:System.Xml.XmlReader> xml 스트림을 통해 xml 데이터에 대 한 noncached, 정방향 전용, 읽기 전용 액세스를 제공 하는 방법을 설명 합니다.

 [XmlWriter를 사용 하 여 XML 작성](https://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) 에서 <xref:System.Xml.XmlWriter> xml 스트림을 생성 하 고 W3C 표준을 준수 하는 xml 문서를 작성할 수 있도록 하는 방법에 대해 설명 합니다.

 [XSLT 변환](https://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) <xref:System.Xml.Xsl.XslCompiledTransform> 클래스가 XSLT 1.0 권장 사항을 구현 하는 방법을 설명 합니다.

 [XPath 데이터 모델을 사용 하 여 XML 데이터 처리](https://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) <xref:System.Xml.XPath.XPathNavigator> 클래스가 또는 개체에 저장 된 XML 데이터를 처리 하는 방법을 설명 합니다 <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> . <xref:System.Xml.XPath.XPathNavigator> 클래스는 XQuery 1.0 및 XPath 2.0 데이터 모델을 기반으로 하며 XML 데이터를 탐색 및 편집하는 데 사용할 수 있습니다.

 [XML SOM (스키마 개체 모델)](https://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) <xref:System.Xml.Schema.XmlSchema> 스키마를 로드 하 고 편집 하는 클래스를 제공 하 여 XML 스키마를 만들고 조작 하는 데 사용 되는 클래스에 대해 설명 합니다.

---
title: XML 데이터로 작업할 때의 보안 고려 사항 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 491e8cf8f9441180e66259ed295e04e8a1a90493
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656134"
---
# <a name="security-considerations-when-working-with-xml-data"></a>XML 데이터 사용 시 보안 고려 사항
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 XML 편집기나 XSLT 디버거로 작업할 때 알아 두어야 할 보안 문제에 대해 설명합니다.

## <a name="xml-editor"></a>XML 편집기
 XML 편집기는 Visual Studio 텍스트 편집기를 기반으로 하며 <xref:System.Xml> 및 <xref:System.Xml.Xsl> 클래스를 사용하여 많은 XML 프로세스를 처리합니다.

- 새 애플리케이션 도메인에서 XSLT 변형이 실행됩니다. XSLT 변형은 ‘샌드박스가 적용’됩니다. 즉, 컴퓨터의 코드 액세스 보안 정책은 XSLT 스타일시트가 있는 위치를 기반으로 제한된 권한을 결정하는 데 사용됩니다. 예를 들어, 인터넷 위치에 있는 스타일시트는 가장 제한된 권한을 갖지만 하드 드라이브에 복사된 스타일시트는 완전 신뢰로 실행됩니다.

- 실행 속도를 향상시키기 위해 <xref:System.Xml.Xsl.XslCompiledTransform> 클래스를 사용하여 XSLT를 MSIL(Microsoft Intermediate Language)로 변환할 수 있습니다.

- XML 편집기에서 처음 로드할 때 카탈로그 파일에서 외부 위치를 가리키는 스키마가 자동으로 다운로드됩니다. <xref:System.Xml.Schema.XmlSchemaSet> 클래스는 스키마를 컴파일하는 데 사용됩니다. XML 편집기와 함께 제공되는 카탈로그 파일에는 외부 스키마의 링크가 없습니다. XML 편집기에서 스키마 파일을 다운로드하기 전에 사용자는 외부 스키마에 대한 참조를 명시적으로 추가해야 합니다. XML 편집기에 대 한 **기타 도구 옵션** 페이지를 통해 HTTP 다운로드를 사용 하지 않도록 설정할 수 있습니다.

- XML 편집기에서는 <xref:System.Net> 클래스를 사용하여 스키마를 다운로드합니다.

## <a name="xslt-debugger"></a>XSLT 디버거
 XSLT 디버거는 관리되는 Visual Studio 디버그 엔진 및 <xref:System.Xml>과 <xref:System.Xml.Xsl> 네임스페이스의 클래스를 사용합니다.

- XSLT 디버거는 샌드박싱된 애플리케이션 도메인에서 각 XSLT 변환을 실행합니다. 컴퓨터의 코드 액세스 보안 정책은 XSLT 스타일시트가 있는 위치를 기반으로 제한된 권한을 결정하는 데 사용됩니다. 예를 들어, 인터넷 위치에 있는 스타일시트는 가장 제한된 권한을 갖지만 하드 드라이브에 복사된 스타일시트는 완전 신뢰로 실행됩니다.

- <xref:System.Xml.Xsl.XslCompiledTransform> 클래스를 사용하여 XSLT 스타일시트가 컴파일됩니다.

- 관리되는 디버그 엔진에서 XSLT 식 계산기를 로드합니다. 관리되는 디버그 엔진은 모든 코드가 사용자의 로컬 컴퓨터에서 실행된다고 가정합니다. 따라서 <xref:System.Xml.Xsl.XslCompiledTransform> 클래스는 XSLT 파일을 사용자의 로컬 컴퓨터로 다운로드합니다. 제한된 권한으로 새 애플리케이션 도메인에서 모든 XSLT 변형을 실행하면 실행 권한을 높일 수 있는 가능성이 적어집니다.

## <a name="see-also"></a>관련 항목
 [애플리케이션 도메인](https://msdn.microsoft.com/39e57d07-a740-4cd4-ae82-e119ea3856c1)

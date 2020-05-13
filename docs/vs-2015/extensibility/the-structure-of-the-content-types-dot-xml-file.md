---
title: Content_types 구조].xml 파일 | 마이크로 소프트 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2d6eca44c08cf35e7b2075965c1b6139e7fb95bc
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395368"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>[Content_types].xml 파일의 구조
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSIX 패키지의 콘텐츠 종류에 대한 정보를 포함합니다. Visual Studio는 [Content_Types].xml 파일을 사용하여 패키지를 설치하지만 파일 자체는 설치하지 않습니다.  
  
> [!NOTE]
> 이 항목은 VSIX 패키지에 사용되는 [Content_Type].xml 파일에만 적용되지만 [Content_Types].xml 파일 형식은 *OPC(개방형 패키징 규칙)* 표준의 일부입니다. 자세한 내용은 OPC: MSDN 웹 사이트에서 [데이터 패키징에 대한 새로운 표준을](https://msdn.microsoft.com/magazine/cc163372.aspx) 참조하십시오.  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 루트 요소와 해당 특성 및 자식 요소를 설명합니다.  
  
### <a name="root-element"></a>루트 요소  
  
|요소|Description|  
|-------------|-----------------|  
|`Types`|VSIX 패키지의 파일 형식을 등록하는 자식 요소를 포함합니다.|  
  
### <a name="attributes"></a>특성  
  
|특성|Description|  
|---------------|-----------------|  
|`Xmlns`|(필수) 이 [Content_Types].xml 파일에 사용되는 스키마의 위치입니다.|  
  
### <a name="attribute-name-attribute"></a>{특성 이름} 특성  
  
|                           값                           |                Description                |
|-----------------------------------------------------------|-------------------------------------------|
| `http://schemas.openformats.org/package/2006/content-types` | 콘텐츠 형식 스키마의 위치입니다. |
  
### <a name="child-elements"></a>자식 요소  
 `Types` 요소는 개수에 관계없이 `Default` 요소를 포함할 수 있습니다.  
  
|요소|Description|  
|-------------|-----------------|  
|`Default`|VSIX 패키지의 콘텐츠 형식에 대해 설명합니다. 패키지의 모든 파일 형식에는 `Default` 고유한 요소가 있어야 합니다.|  
  
### <a name="attributes"></a>특성  
  
|특성|Description|  
|---------------|-----------------|  
|`Extension`|VSIX 패키지에 있는 파일의 파일 이름 확장명입니다.|  
|`ContentType`|파일 이름 확장명과 연결된 콘텐츠의 종류를 설명합니다.|  
  
### <a name="attribute-name-attribute"></a>{특성 이름} 특성  
 Visual Studio는 연결된 `ContentType` `Extension` 형식에 대한 다음 값을 인식합니다.  
  
|내선 번호|ContentType|  
|---------------|-----------------|  
|txt|텍스트/일반|  
|pkgdef|텍스트/일반|  
|Xml|text/xml|  
|vsixmanifest|text/xml|  
|htm 또는 html|텍스트/html|  
|Rtf|응용 프로그램 / RTF|  
|pdf|응용 프로그램 / PDF|  
|GIF|image/gif|  
|jpg 또는 jpeg|이미지 /jpg|  
|tiff|image/tiff|  
|vsix|응용 프로그램 / 우편|  
|zip|응용 프로그램 / 우편|  
|dll|application/octet-stream|  
|다른 모든 파일 형식|application/octet-stream|  
  
## <a name="example"></a>예제  
  
### <a name="description"></a>Description  
 다음 [Content_Types].xml 파일은 일반적인 VSIX 패키지를 설명합니다.  
  
### <a name="code"></a>코드  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
    <Default Extension="vsixmanifest" ContentType="text/xml" />   
    <Default Extension="dll" ContentType="application/octet-stream" />   
    <Default Extension="png" ContentType="application/octet-stream" />   
    <Default Extension="txt" ContentType="text/plain" />   
    <Default Extension="pkgdef" ContentType="text/plain" />   
</Types>  
```  
  
## <a name="see-also"></a>관련 항목  
 [VSIX 패키지의 해부학](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX 확장 스키마 1.0 참조](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: 데이터 패키징을 위한 새로운 표준](https://msdn.microsoft.com/magazine/cc163372.aspx)

---
title: '[Content_types].xml 파일 | Microsoft Docs'
description: VSIX 패키지의 콘텐츠 종류에 대한 정보를 포함하는 콘텐츠 형식 파일의 구조에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 96d4d0eeea34300894674a2105d080e8a6abb607
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900423"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>[Content_types].xml 파일의 구조
VSIX 패키지의 콘텐츠 종류에 대한 정보를 포함합니다. Visual Studio [Content_Types].xml 파일을 사용하여 패키지를 설치하지만 파일 자체는 설치하지 않습니다.

> [!NOTE]
> 이 항목은 VSIX 패키지에 사용되는 [Content_Type].xml 파일에만 적용되지만 [Content_Types].xml 파일 형식은 *OPC(Open Packaging Conventions)* 표준의 일부입니다. 자세한 내용은 OPC: MSDN 웹 사이트에서 [데이터를 패키징하기 위한 새로운 표준을 참조하세요.](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data)

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 루트 요소와 해당 특성 및 자식 요소에 대해 설명합니다.

### <a name="root-element"></a>루트 요소

|요소|설명|
|-------------|-----------------|
|`Types`|VSIX 패키지의 파일 형식을 열거하는 자식 요소를 포함합니다.|

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|`Xmlns`|(필수) 이 [Content_Types].xml 파일에 사용되는 스키마의 위치입니다.|

### <a name="attribute-name-attribute"></a>{특성 이름} 특성

| 값 | 설명 |
| - | - |
| `http://schemas.openformats.org/package/2006/content-types` | 콘텐츠 형식 스키마의 위치입니다. |

### <a name="child-elements"></a>자식 요소
 `Types` 요소는 개수에 관계없이 `Default` 요소를 포함할 수 있습니다.

|요소|설명|
|-------------|-----------------|
|`Default`|VSIX 패키지의 콘텐츠 형식에 대해 설명합니다. 패키지의 모든 파일 형식에는 고유한 요소가 있어야 `Default` 합니다.|

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|`Extension`|VSIX 패키지에 있는 파일의 파일 이름 확장명입니다.|
|`ContentType`|파일 이름 확장명과 연결된 콘텐츠의 종류에 대해 설명합니다.|

### <a name="attribute-name-attribute"></a>{특성 이름} 특성
 Visual Studio 연결된 형식에 대해 다음 `ContentType` 값을 `Extension` 인식합니다.

|확장|ContentType|
|---------------|-----------------|
|txt|텍스트/일반|
|pkgdef|텍스트/일반|
|Xml|text/xml|
|vsixmanifest|text/xml|
|htm 또는 html|텍스트/html|
|Rtf|application/rtf|
|pdf|application/pdf|
|GIF|image/gif|
|jpg 또는 jpeg|image/jpg|
|tiff|image/tiff|
|vsix|application/zip|
|zip|application/zip|
|dll|application/octet-stream|
|다른 모든 파일 형식|application/octet-stream|

## <a name="example"></a>예제

### <a name="description"></a>설명
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

## <a name="see-also"></a>참조
- [VSIX 패키지 분석](../extensibility/anatomy-of-a-vsix-package.md)
- [VSIX 확장 스키마 1.0 참조](/previous-versions/dd393700(v=vs.110))
- [OPC: 데이터 패키징을 위한 새로운 표준](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data)
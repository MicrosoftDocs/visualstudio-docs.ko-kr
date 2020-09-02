---
title: '[Content_types] .xml 파일의 구조입니다. Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2761e012d32516265e61c8001491e3c605372ff5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699029"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>[Content_types].xml 파일의 구조
VSIX 패키지의 콘텐츠 종류에 대 한 정보를 포함 합니다. Visual Studio는 [Content_Types] .xml 파일을 사용 하 여 패키지를 설치 하지만 파일 자체를 설치 하지는 않습니다.

> [!NOTE]
> 이 항목은 VSIX 패키지에 사용 되는 [Content_Type] .xml 파일에만 적용 되기는 하지만 [Content_Types] .xml 파일 형식은 *OPC (Open 패키징 규칙)* 표준의 일부입니다. 자세한 내용은 OPC: MSDN 웹 사이트에서 [데이터를 패키징하는 새 표준](https://msdn.microsoft.com/magazine/cc163372.aspx) 을 참조 하세요.

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 루트 요소와 해당 특성 및 자식 요소에 대해 설명 합니다.

### <a name="root-element"></a>루트 요소

|요소|설명|
|-------------|-----------------|
|`Types`|VSIX 패키지의 파일 형식을 열거 하는 자식 요소를 포함 합니다.|

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|`Xmlns`|필요 합니다. 이 [Content_Types] .xml 파일에 사용 되는 스키마의 위치입니다.|

### <a name="attribute-name-attribute"></a>{Attribute name} 특성도

| 값 | 설명 |
| - | - |
| `http://schemas.openformats.org/package/2006/content-types` | 콘텐츠 형식 스키마의 위치입니다. |

### <a name="child-elements"></a>자식 요소
 `Types` 요소는 개수에 관계없이 `Default` 요소를 포함할 수 있습니다.

|요소|설명|
|-------------|-----------------|
|`Default`|VSIX 패키지의 콘텐츠 형식을 설명 합니다. 패키지의 모든 파일 형식에는 고유한 요소가 있어야 합니다 `Default` .|

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|`Extension`|VSIX 패키지에 있는 파일의 파일 이름 확장명입니다.|
|`ContentType`|파일 이름 확장명과 연결 된 콘텐츠의 종류를 설명 합니다.|

### <a name="attribute-name-attribute"></a>{Attribute name} 특성도
 Visual Studio에서는 연결 된 `ContentType` 형식에 대해 다음 값을 인식 합니다 `Extension` .

|확장명|ContentType|
|---------------|-----------------|
|txt|텍스트/일반|
|.pkgdef|텍스트/일반|
|Xml|text/xml|
|source.extension.vsixmanifest|text/xml|
|htm 또는 html|텍스트/html|
|형식|응용 프로그램/rtf|
|pdf|응용 프로그램/pdf|
|GIF|image/gif|
|jpg 또는 jpeg|이미지/jpg|
|tiff|image/tiff|
|vsix|응용 프로그램/zip|
|zip|응용 프로그램/zip|
|dll|application/octet-stream|
|기타 모든 파일 형식|application/octet-stream|

## <a name="example"></a>예제

### <a name="description"></a>설명
 다음 [Content_Types] .xml 파일은 일반적인 VSIX 패키지를 설명 합니다.

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
- [VSIX 확장 스키마 1.0 참조](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [OPC: 데이터를 패키징하는 새 표준](https://msdn.microsoft.com/magazine/cc163372.aspx)

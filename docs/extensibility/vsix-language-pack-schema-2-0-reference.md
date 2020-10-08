---
title: VSIX 언어 팩 스키마 2.0 참조 | Microsoft Docs
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
author: acangialosi
ms.author: anthc
manager: jillfra
ms.openlocfilehash: f0eee51c0654c6e517209e23baf43c6b262d8f73
ms.sourcegitcommit: c31815e140f2ec79e00a9a9a19900778ec11e860
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91830707"
---
# <a name="vsix-language-pack-schema-20-reference"></a>VSIX 언어 팩 스키마 2.0 참조

VSIX 언어 팩 스키마는 VSIX 패키지에 대 한 지역화 된 설치 정보를 제공 합니다. 이 스키마의 버전 2.0은 추가 지역화 요소를 지원 합니다.

## <a name="language-pack-schema"></a>언어 팩 스키마

언어 팩 파일의 루트 요소는 이며 `<PackageLanguagePackManifest>` `Version` 언어 팩 형식의 버전인 특성을 사용 합니다. 이 문서에서는 특성을 값으로 설정 하 여 매니페스트에 지정 된 언어 팩 형식의 버전 2.0을 설명 합니다 `Version` `Version="2.0.0"` . 루트 요소는 정확히 하나의 자식 요소를 포함 합니다 `<Metadata>` .

### <a name="packagelanguagepackmanifest-element"></a>PackageLanguagePackManifest 요소

요소 내에 `<PackageLanguagePackManifest>` 다음 요소가 있어야 합니다.

|제목|Description|
|-----------|-----------------|
|`<Metadata>`| 모든 지역화 된 패키지 메타 데이터에 대 한 포함 요소입니다.

### <a name="metadata-element"></a>Metadata 요소

요소 내에 `<Metadata>` 다음 요소를 사용할 수 있습니다.

|제목|Description|
|-----------|-----------------|
|`<DisplayName>`|설치할 확장의 지역화 된 이름입니다.|
|`<Description>`|설치할 확장에 대 한 지역화 된 설명입니다.|
|`<License>`| 확장 라이선스의 지역화 된 버전에 대 한 경로입니다.|
|`<MoreInfo>`| 확장에 대 한 지역화 된 정보에 대 한 링크입니다.|
|`<ReleaseNotes>`| 릴리스 정보의 지역화 된 버전에 대 한 경로 또는 링크|
|`<Icon>`| 확장명 아이콘의 지역화 된 버전에 대 한 경로입니다.|

### <a name="sample-manifest"></a>샘플 매니페스트

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>참조

|제목|Description|
|-----------|-----------------|
|[VSIX 패키지 지역화](../extensibility/localizing-vsix-packages.md)|VSIX 패키지에 대해 지역화 된 설치 지원을 제공 하는 방법을 보여 줍니다.|
|[VSIX 확장 스키마 2.0 참조](../extensibility/vsix-extension-schema-2-0-reference.md)|VSIX 매니페스트는 *.vsix* 배포 파일의 콘텐츠를 설명 합니다. 배포 파일을 사용 하면 **확장 및 업데이트** 대화 상자를 사용 하 여 Visual Studio 확장을 설치할 수 있습니다.|
|[Visual Studio 확장 찾기 및 사용](../ide/finding-and-using-visual-studio-extensions.md)|확장 **및 업데이트** 대화 상자를 사용 하 여 확장을 설치, 제거, 활성화 및 비활성화 하는 방법을 보여 줍니다.|

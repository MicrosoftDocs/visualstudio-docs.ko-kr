---
title: VSIX 패키지 현지화 | 마이크로 소프트 문서
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d2d4222e45d56447951e86d558af9983a0d1cc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702893"
---
# <a name="localizing-vsix-packages"></a>VSIX 패키지 지역화

각 대상 언어에 대해 *Extension.vsixlangpack* 파일을 만든 다음 올바른 폴더에 배치하여 VSIX 패키지를 지역화할 수 있습니다. 지역화된 패키지가 설치되면 지역화된 설명과 함께 확장의 지역화된 이름이 표시됩니다. 지역화된 라이센스 파일 또는 지역화된 정보를 가리키는 URL을 제공하는 경우 해당 파일도 표시됩니다.

VSIX 패키지에 메뉴 명령 이나 다른 UI를 추가 하는 VSPackage 포함 하는 콘텐츠 경우 새 UI 요소를 지역화에 대 한 자세한 내용은 [메뉴 지정 명령을](../extensibility/localizing-menu-commands.md) 참조 하십시오.

## <a name="directory-structure"></a>디렉터리 구조

 사용자가 확장을 설치하면 확장 및 업데이트는 VSIX 패키지의 최상위 수준에서 이름이 대상 컴퓨터의 Visual Studio 로캘과 일치하는 폴더를 **검사합니다.** **확장 및 업데이트가** 폴더에서 *.vsixlangpack* 파일을 찾으면 해당 파일의 지역화된 값을 *.vsixmanifest* 파일의 해당 값으로 대체합니다. 이러한 값은 확장을 설치할 때 표시됩니다. 다음 예제에서는 스페인어(es-ES) 및 프랑스어(fr-FR)로 지역화된 VSIX 패키지의 디렉터리 구조를 보여 주십니다.

```text
.
├── MyExtension.dll
├── Extension.vsixmanifest
├── [Content_Types].xml
├── es-ES
│   └── Extension.vsixlangpack
└── fr-FR
    └── Extension.vsixlangpack
```

> [!NOTE]
> VSIX 지원 프로젝트 템플릿은 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] VSIX 매니페스트를 생성하고 *이름을 source.extension.vsixmanifest*. Visual Studio에서 프로젝트를 빌드하면 해당 파일의 내용을 VSIX 패키지의 Extension.VsixManifest에 복사합니다.

## <a name="the-extensionvsixlangpack-file"></a>확장.vsixlangpack 파일

*Extension.vsixlangpack* 파일은 [VSIX 언어 팩 스키마 2.0을](../extensibility/vsix-language-pack-schema-2-0-reference.md)따릅니다. 이 스키마에는 `PackageLanguagePackManifest`즉시 자식 요소가 `Metadata` 뒤에 올 수 있는 . 메타데이터 요소에는 최대 6개의 `DisplayName`자식 요소, , `Description`" `MoreInfo` `License` `ReleaseNotes`및 `Icon`. 이러한 자식 요소는 `DisplayName` `Description` `MoreInfo` *Extension.vsixmanifest* 파일의 `Metadata` 요소의 " 및 `License` `ReleaseNotes` `Icon` 자식 요소에 해당합니다.

vsixlangpack 파일을 만들 때 `Include in Vsix` 속성을 `true`로 설정해야 합니다. 그렇지 않으면 지역화된 설치 텍스트가 무시됩니다.

### <a name="to-set-the-include-in-vsix-property"></a>Vsix에 포함을 설정하려면

1. **솔루션 탐색기에서**Extension.vsixlangpack 파일을 마우스 오른쪽 단추로 클릭한 다음 **속성을**클릭합니다.

2. 속성 **그리드에서** **V6에 포함을**클릭하고 값을 `true`로 설정합니다.

## <a name="example"></a>예제

### <a name="description"></a>설명

다음 예제에서는 *Extension.vsixmanifest* 파일의 관련 부분을 보여 주다. 이 파일에는 스페인어에 해당하는 *Extension.vsixlangpack* 파일도 포함되어 있습니다. 대상 컴퓨터의 Visual Studio 로캘이 스페인어로 설정된 경우 언어 팩의 값이 매니페스트의 값을 대체합니다.

### <a name="code"></a>코드

- [*익스텐션.vsixmanifest*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest ...>
  <Metadata ...>
    <DisplayName>Family Tree</DisplayName>
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>
    <MoreInfo>http://www.contoso.com/products/FamilyTree.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
  <Installation .../>
  <Dependencies .../>
  <Prerequisites .../>
  <Assets .../>
</PackageManifest>
```

- [*익스텐션.vsixlangpack*]

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

|제목|설명|
|-----------|-----------------|
|[VSIX 언어 팩 스키마 2.0 참조](vsix-language-pack-schema-2-0-reference.md)|VSIX 언어 팩은 .vsix 배포 파일의 지역화 정보를 설명합니다.|
|[VSIX 패키지의 해부학](../extensibility/anatomy-of-a-vsix-package.md)|vsix 패키지의 구조와 내용을 설명합니다.|
|[메뉴 명령 지역화](../extensibility/localizing-menu-commands.md)|확장에서 다른 텍스트 리소스를 지역화하는 방법을 보여 주면 됩니다.|

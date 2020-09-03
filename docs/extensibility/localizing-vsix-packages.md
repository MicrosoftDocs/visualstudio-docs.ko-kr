---
title: VSIX 패키지 지역화 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702893"
---
# <a name="localizing-vsix-packages"></a>VSIX 패키지 지역화

각 대상 언어에 대 한 *확장명 vsixlangpack* 파일을 만든 다음 올바른 폴더에 배치 하 여 VSIX 패키지를 지역화할 수 있습니다. 지역화 된 패키지가 설치 되 면 확장의 지역화 된 이름이 지역화 된 설명과 함께 표시 됩니다. 지역화 된 라이선스 파일이 나 지역화 된 정보를 가리키는 URL을 제공 하는 경우에도 표시 됩니다.

VSIX 패키지에 메뉴 명령이 나 기타 UI를 추가 하는 VSPackage 포함 되어 있는 경우 새 UI 요소를 지역화 하는 방법에 대 한 자세한 내용을 보려면 [메뉴 명령 지역화](../extensibility/localizing-menu-commands.md) 를 참조 하세요.

## <a name="directory-structure"></a>디렉터리 구조

 사용자가 확장을 설치할 때 **확장 및 업데이트** 는 대상 컴퓨터의 Visual Studio 로캘과 이름이 일치 하는 폴더에 대 한 VSIX 패키지의 최상위 수준을 확인 합니다. **확장명 및 업데이트** 는 폴더에서 *vsixlangpack* 파일을 찾은 경우 해당 파일의 지역화 된 값을 *source.extension.vsixmanifest* 파일의 해당 값으로 대체 합니다. 확장을 설치 하는 경우 이러한 값이 표시 됩니다. 다음 예에서는 스페인어 (es) 및 프랑스어 (fr-fr)로 지역화 된 VSIX 패키지의 디렉터리 구조를 보여 줍니다.

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
> 에서 VSIX 지원 프로젝트 템플릿은 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] vsix 매니페스트를 생성 하 고 이름을 *source.extension.vsixmanifest*로 만듭니다. Visual Studio는 프로젝트를 빌드할 때 VSIX 패키지의 Source.extension.vsixmanifest에 해당 파일의 콘텐츠를 복사 합니다.

## <a name="the-extensionvsixlangpack-file"></a>확장명 vsixlangpack 파일

*확장명 vsixlangpack* 파일은 [VSIX 언어 팩 스키마 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md)을 따릅니다. 이 스키마에는 `PackageLanguagePackManifest` 바로 다음에 자식 요소가 있는가 있습니다 `Metadata` . Metadata 요소는 자식 요소,,,,, 및를 최대 6 개까지 포함할 수 있습니다 `DisplayName` `Description` `MoreInfo` `License` `ReleaseNotes` `Icon` . 이러한 자식 요소는 `DisplayName` source.extension.vsixmanifest 파일에 있는 요소의,, `Description` ,, `MoreInfo` `License` `ReleaseNotes` 및 자식 요소에 해당 `Icon` `Metadata` 합니다 *Extension.vsixmanifest* .

Vsixlangpack 파일을 만들 때 속성을로 설정 해야 합니다 `Include in Vsix` `true` . 그렇지 않으면 지역화 된 설치 텍스트가 무시 됩니다.

### <a name="to-set-the-include-in-vsix-property"></a>Vsix에 포함 속성을 설정 하려면

1. **솔루션 탐색기**에서 확장명 vsixlangpack 파일을 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다.

2. **속성 표에서** **Vsix에 포함**을 클릭 하 고 해당 값을로 설정 `true` 합니다.

## <a name="example"></a>예제

### <a name="description"></a>설명

다음 예제에서는 *source.extension.vsixmanifest* 파일의 관련 부분을 보여 줍니다. 이 파일에는 스페인어 용 *vsixlangpack* 파일도 포함 되어 있습니다. 대상 컴퓨터의 Visual Studio 로캘이 스페인어로 설정 된 경우 언어 팩의 값이 매니페스트에서 값을 대체 합니다.

### <a name="code"></a>코드

- [*확장. source.extension.vsixmanifest*]

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

- [*확장명. vsixlangpack*]

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
|[VSIX 언어 팩 스키마 2.0 참조](vsix-language-pack-schema-2-0-reference.md)|VSIX 언어 팩은 .vsix 배포 파일의 지역화 정보에 대해 설명 합니다.|
|[VSIX 패키지 분석](../extensibility/anatomy-of-a-vsix-package.md)|Vsix 패키지의 구조 및 내용에 대해 설명 합니다.|
|[메뉴 명령 지역화](../extensibility/localizing-menu-commands.md)|확장에서 다른 텍스트 리소스를 지역화 하는 방법을 보여 줍니다.|

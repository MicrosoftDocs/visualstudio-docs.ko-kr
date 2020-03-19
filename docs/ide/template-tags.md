---
title: 프로젝트 템플릿에 태그 추가 또는 편집
description: Visual Studio에서 프로젝트 템플릿의 태그를 추가 또는 편집하는 방법에 대해 알아보세요.
ms.date: 04/30/2019
author: minsa110
ms.author: somin
manager: jillfra
ms.topic: reference
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
- template tagging, updating
- template tags, updating
ms.openlocfilehash: 37fa5449847eb4c093475df11a07decb31168f1f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "73189514"
---
# <a name="add-tags-to-project-templates"></a>프로젝트 템플릿에 태그 추가

[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) 버전 16.1 미리 보기 2부터는 언어, 플랫폼 및 프로젝트 형식 태그를 프로젝트 템플릿에 추가할 수 있습니다. 

태그는 **새 프로젝트** 대화 상자의 두 위치에서 사용됩니다.

- 태그는 템플릿 설명 아래에 표시됩니다.

   ![새 프로젝트 대화 상자에 태그를 포함한 프로젝트 템플릿](media/npd-item-with-template-tags.png)

- 태그를 사용하여 템플릿을 검색 및 필터링할 수 있습니다.

   ![새 프로젝트 대화 상자에서 검색 및 필터링](media/npd-search-and-filter.png)

*.vstemplate* XML 파일을 업데이트하여 태그를 추가할 수 있습니다. Visual Studio에 기본 제공되는 템플릿 태그를 사용하거나 사용자 지정 템플릿 태그를 만들 수 있습니다. 템플릿 태그는 Visual Studio 2019 **새 프로젝트** 대화 상자에만 나타납니다. 템플릿 태그는 이전 버전의 Visual Studio에서 템플릿의 렌더링 방법에 영향을 주지 않습니다.

## <a name="add-or-edit-tags"></a>태그 추가 또는 편집

다음 중 한 가지 작업을 수행하는 경우 프로젝트 템플릿의 *.vstemplate* XML에서 태그를 추가 또는 편집할 수 있습니다.

* 템플릿 내보내기 마법사를 사용하여 [새 프로젝트 템플릿 만들기](how-to-create-project-templates.md)
* [기존 프로젝트 템플릿 업데이트](how-to-update-existing-templates.md)
* [새 VSIX 프로젝트 템플릿 만들기](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="syntax"></a>구문

```xml
<LanguageTag> Language Name </LanguageTag>
<PlatformTag> Platform Name </PlatformTag>
<ProjectTypeTag> Project Type </ProjectTypeTag>
```

## <a name="attributes"></a>특성

고급 사용자 시나리오에서 다음 선택적 특성을 사용할 수 있습니다.

|attribute|Description|
|---------------|-----------------|
|`Package`|Visual Studio 패키지를 ID를 지정하는 GUID입니다.|
|`ID`|Visual Studio 리소스 ID를 지정합니다.|

구문

```xml
<LanguageTag Package="{PackageID}" ID="ResourceID" />
<PlatformTag Package="{PackageID}" ID="ResourceID" />
<ProjectTypeTag Package="{PackageID}" ID="ResourceID" />
```

## <a name="elements"></a>요소

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|(필수) 템플릿을 분류하고 **새 프로젝트** 대화 상자 또는 **새 항목 추가** 대화 상자에서 템플릿이 표시되는 방식을 정의합니다.|

## <a name="text-value"></a>텍스트 값

`Package` 및 `ID` 특성을 사용하는 경우가 아니면 텍스트 값은 필수입니다.

텍스트는 템플릿의 이름을 제공합니다.

## <a name="built-in-tags"></a>기본 제공 태그

Visual Studio는 기본 제공되는 태그의 목록을 제공합니다. 기본 제공 태그를 추가하면 태그는 현지화된 리소스를 렌더링합니다. 

다음은 Visual Studio에서 사용할 수 있는 기본 제공 태그를 보여 줍니다. 해당 값은 괄호 안에 표시됩니다.

| 언어 | 플랫폼 | 프로젝트 형식 |
| -- | -- | -- |
| C++(`cpp`) | Android(`android`) | 클라우드(`cloud`) |
| C#(`csharp`) | Azure(`azure`) | 콘솔(`console`) |
| F#(`fsharp`) | iOS(`ios`) | 바탕 화면(`desktop`) |
| Java(`java`) | Linux(`linux`) | 확장 기능(`extension`) |
| JavaScript(`javascript`) | macOS(`macos`) | 게임(`games`) |
| Python(`python`) | tvOS(`tvos`) | IoT(`iot`) |
| 쿼리 언어(`querylanguage`) | Windows(`windows`) | 라이브러리(`library`) |
| TypeScript(`typescript`) | Xbox(`xbox`) | 기계 학습(`machinelearning`) |
| Visual Basic(`visualbasic`) | | 모바일(`mobile`) |
| | | Office(`office`) |
| | | 기타(`other`) |
| | | 서비스(`service`) |
| | | 테스트(`test`) |
| | | UWP(`uwp`) |
| | | 웹(`web`) |

## <a name="example"></a>예제

다음 예제는 Visual C# 애플리케이션의 프로젝트 템플릿용 메타데이터를 보여 줍니다.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <LanguageTag>C#</LanguageTag>
        <PlatformTag>windows</PlatformTag>
        <PlatformTag>linux</PlatformTag>
        <PlatformTag>My Platform</PlatformTag>
        <ProjectTypeTag>console</ProjectTypeTag>
        <ProjectTypeTag>desktop</ProjectTypeTag>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>참고 항목

- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](creating-project-and-item-templates.md)
- [프로젝트 및 항목 템플릿 사용자 지정](customizing-project-and-item-templates.md)
- [VSIX 프로젝트 템플릿 시작](../extensibility/getting-started-with-the-vsix-project-template.md)

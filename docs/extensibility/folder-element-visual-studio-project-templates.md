---
title: 폴더 요소(비주얼 스튜디오 프로젝트 템플릿) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb256b8be0dd9ce68f193750bf3ff5a383d5f073
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711460"
---
# <a name="folder-element-visual-studio-project-templates"></a>폴더 요소(Visual Studio 프로젝트 템플릿)
프로젝트에 추가될 폴더를 지정합니다.

 \<VS템플릿 \<> 템플릿콘텐츠 \< \<> 프로젝트> 폴더>

## <a name="syntax"></a>구문

```
<Folder Name="Project Folder">
    <Folder> ... </Folder>
    <ProjectItem> ... </ProjectItem>
</Folder>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|`Name`|필수 특성입니다.<br /><br /> 프로젝트 폴더의 이름입니다.|
|`TargetFolderName`|선택적 특성입니다.<br /><br /> 템플릿에서 프로젝트를 만들 때 폴더를 지정합니다. 이 특성은 매개 변수 대체를 사용하여 폴더 이름을 만들거나 *.zip* 파일에서 직접 사용할 수 없는 국제 문자열로 폴더이름을 지정하는 데 유용합니다.|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|`Folder`|프로젝트에 추가할 폴더를 지정합니다. `Folder`요소에는 자식 `Folder` 요소가 포함될 수 있습니다.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|프로젝트에 추가할 파일을 지정합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[프로젝트](../extensibility/project-element-visual-studio-templates.md)|템플릿의 선택적 자식 [요소콘텐츠](../extensibility/templatecontent-element-visual-studio-templates.md).|

## <a name="remarks"></a>설명
 `Folder`은 의 선택적 `Project`자식입니다.

 다음 방법 중 한 가지를 사용하여 프로젝트 항목을 템플릿의 폴더로 구성할 수 있습니다.

- 템플릿 *.zip* 파일에 폴더를 포함하고 요소가 없는 `ProjectItem` `Folder` 요소의 파일에 대한 경로를 지정하여 *.vstemplate* 파일의 프로젝트에 추가합니다. 이것이 권장된 방법입니다. 다음은 그 예입니다.

     `...`

     `<ProjectItem>\Folder\item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- 템플릿 *.zip* 파일에 폴더를 포함하고 요소가 있는 `Folder` *.vstemplate* 파일의 프로젝트에 추가합니다. 다음은 그 예입니다.

     `...`

     `<Folder name="Folder">`

     `<ProjectItem>item.cs</ProjectItem>`

     `</Folder>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- 템플릿 *.zip* 파일에 폴더를 포함하지 말고 요소의 특성을 `TargetFileName` 사용하여 `ProjectItem` 폴더를 추가하십시오. 다음은 그 예입니다.

     `...`

     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

## <a name="example"></a>예제
 다음 예제에서는 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Windows 응용 프로그램에 대 한 프로젝트 템플릿에 대 한 메타 데이터를 보여 줍니다.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <Folder Name="Properties">
                <ProjectItem>AssemblyInfo.cs</ProjectItem>
                <ProjectItem>Resources.resx</ProjectItem>
                <ProjectItem>Resources.Designer.cs</ProjectItem>
                <ProjectItem>Settings.settings</ProjectItem>
                <ProjectItem>Settings.Designer.cs</ProjectItem>
            </Folder>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>참조
- [비주얼 스튜디오 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [ProjectItem 요소(비주얼 스튜디오 항목 템플릿)](../extensibility/projectitem-element-visual-studio-item-templates.md)

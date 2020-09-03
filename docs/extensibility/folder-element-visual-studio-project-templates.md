---
title: Folder 요소 (Visual Studio 프로젝트 템플릿) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
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
ms.openlocfilehash: b05ef44896e5cd428584c7efed267f130597ee35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85769586"
---
# <a name="folder-element-visual-studio-project-templates"></a>Folder 요소 (Visual Studio 프로젝트 템플릿)
프로젝트에 추가 될 폴더를 지정 합니다.

 \<VSTemplate> \<TemplateContent>
 \<Project>
 \<Folder>

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

|특성|설명|
|---------------|-----------------|
|`Name`|필수 특성입니다.<br /><br /> 프로젝트 폴더의 이름입니다.|
|`TargetFolderName`|선택적 특성입니다.<br /><br /> 템플릿에서 프로젝트를 만들 때 폴더에 지정할 이름을 지정 합니다. 이 특성은 매개 변수 대체를 사용 하 여 폴더 이름을 만들거나 *.zip* 파일에서 직접 사용할 수 없는 국제 문자열로 폴더 이름을 지정 하는 데 유용 합니다.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|`Folder`|프로젝트에 추가할 폴더를 지정 합니다. `Folder` 요소에는 자식 요소가 포함 될 수 있습니다 `Folder` .|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|프로젝트에 추가할 파일을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[프로젝트](../extensibility/project-element-visual-studio-templates.md)|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)의 선택적 자식 요소입니다.|

## <a name="remarks"></a>설명
 `Folder` 은의 선택적 자식 요소입니다 `Project` .

 다음 방법 중 하나를 사용 하 여 프로젝트 항목을 템플릿에서 폴더로 구성할 수 있습니다.

- 템플릿 *.zip* 파일에 폴더를 포함 하 고 요소 없이 요소에 파일의 경로를 지정 하 여 *.vstemplate* 파일의 프로젝트에 추가 합니다. `ProjectItem` `Folder` 이것이 권장된 방법입니다. 예를 들면 다음과 같습니다.

     `...`

     `<ProjectItem>\Folder\item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- 템플릿 *.zip* 파일에 폴더를 포함 하 고 *.vstemplate* 파일의 요소를 사용 하 여 프로젝트에 추가 합니다. `Folder` 예를 들면 다음과 같습니다.

     `...`

     `<Folder name="Folder">`

     `<ProjectItem>item.cs</ProjectItem>`

     `</Folder>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- 템플릿 *.zip* 파일에 폴더를 포함 하지 않고 요소의 특성을 사용 하 여 폴더를 추가 `TargetFileName` `ProjectItem` 합니다. 예를 들어:

     `...`

     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

## <a name="example"></a>예제
 다음 예제에서는 Windows 응용 프로그램에 대 한 프로젝트 템플릿에 대 한 메타 데이터를 보여 줍니다 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

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
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [ProjectItem 요소 (Visual Studio 항목 템플릿)](../extensibility/projectitem-element-visual-studio-item-templates.md)

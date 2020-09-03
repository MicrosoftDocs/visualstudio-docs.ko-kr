---
title: Project 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 335a1e4efa62f07e10bb24b9971627d24bb13273
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702000"
---
# <a name="project-element-visual-studio-templates"></a>Project 요소 (Visual Studio 템플릿)
프로젝트에 추가할 파일 또는 디렉터리를 지정 합니다.

 \<VSTemplate> \<TemplateContent>
 \<Project>

## <a name="syntax"></a>구문

```
<Project
    File="MyProject.proj"
    TargetFileName="MyTargetProject.proj"
    ReplaceParameters="true/false">
    IgnoreProjectParameter="$myCustomParameter$"
        ...
</Project>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|`File`|필수 특성입니다.<br /><br /> 템플릿 *.zip* 파일에 있는 프로젝트 파일의 이름을 지정 합니다.|
|`ReplaceParameters`|선택적 특성입니다.<br /><br /> 프로젝트 파일에 템플릿에서 프로젝트를 만들 때 교체 해야 하는 매개 변수 값이 있는지 여부를 지정 하는 부울 값입니다. 기본값은 `false`여야 합니다.|
|`TargetFileName`|선택적 특성입니다.<br /><br /> 템플릿에서 프로젝트를 만들 때 프로젝트 파일의 이름을 지정 합니다.|
|`IgnoreProjectParameter`|선택적 특성입니다.<br /><br /> 프로젝트를 현재 솔루션에 추가할지 여부를 지정 합니다. 사용자 지정 매개 변수 값 "$*Mycustomparameter*$"가 매개 변수 대체 파일에 있으면 프로젝트가 만들어지지만 현재 열려 있는 솔루션의 일부로 추가 되지 않습니다.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[폴더](../extensibility/folder-element-visual-studio-project-templates.md)|선택적 요소입니다.<br /><br /> 프로젝트에 추가할 폴더를 지정 합니다.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|선택적 요소입니다.<br /><br /> 프로젝트에 추가할 파일을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|필수적 요소입니다.|

## <a name="remarks"></a>설명
 `Project`은 `TemplateContent`의 선택적 자식 요소입니다.

 요소는 프로젝트를 지정할 때 `Project` 사용 되므로 프로젝트 템플릿에만 사용할 수 있습니다.

 `Project`요소에는 자식 요소 또는 [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) 자식 [요소가 있을 수](../extensibility/folder-element-visual-studio-project-templates.md) 있지만이 요소와 자식 요소를 함께 사용할 수는 없습니다 `Folder` `ProjectItem` .

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]**새 프로젝트** 대화 상자에서 사용자가 입력 한 이름에 따라 프로젝트 파일 이름의 이름을 자동으로 바꿉니다. `TargetFileName`템플릿을 사용 하 여 만든 프로젝트 파일에 대 한 대체 파일 이름을 제공 하려는 경우 특성을 사용 합니다.

## <a name="example"></a>예
 다음 예제에서는 응용 프로그램에 대 한 프로젝트 템플릿에 대 한 메타 데이터를 보여 줍니다 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
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

## <a name="see-also"></a>참조
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [ProjectItem 요소 (Visual Studio 프로젝트 템플릿)](../extensibility/projectitem-element-visual-studio-project-templates.md)
- [Folder 요소 (Visual Studio 프로젝트 템플릿)](../extensibility/folder-element-visual-studio-project-templates.md)

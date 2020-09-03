---
title: ProjectCollection 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectCollection
helpviewer_keywords:
- <ProjectCollection> element [Visual Studio Templates]
- ProjectCollection element [Visual Studio Templates]
ms.assetid: deb27180-2035-49ed-b835-c47bb3cd2f8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 12a22ca28c90ed1df69529ed3004b417b5e04276
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701969"
---
# <a name="projectcollection-element-visual-studio-templates"></a>ProjectCollection 요소 (Visual Studio 템플릿)
다중 프로젝트 템플릿의 구성과 내용을 지정합니다.

 \<VSTemplate> \<TemplateContent>
 \<ProjectCollection>

## <a name="syntax"></a>구문

```xml
<ProjectCollection>
    <ProjectTemplateLink> ... </ProjectTemplateLink>
    <SolutionFolder> ... </SolutionFolder>
</ProjectCollection>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> 다중 프로젝트 템플릿의 프로젝트를 지정 합니다.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> 다중 프로젝트 템플릿의 프로젝트를 그룹화합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 템플릿의 내용을 지정 합니다.|

## <a name="remarks"></a>설명
 다중 프로젝트 템플릿은 두 개 이상의 프로젝트에 대한 컨테이너로 사용됩니다. `ProjectCollection`요소는 템플릿에 포함할 프로젝트를 지정 하는 데 사용 됩니다. 다중 프로젝트 템플릿에 대 한 자세한 내용은 [방법: 다중 프로젝트 템플릿 만들기](../ide/how-to-create-multi-project-templates.md)를 참조 하세요.

## <a name="example"></a>예제
 이 예제에서는 간단한 다중 프로젝트 루트 *.vstemplate* 파일을 보여 줍니다. 이 예제에서 템플릿에는 `My Windows Application` 프로젝트와 `My Class Library` 프로젝트가 들어 있습니다. `ProjectName` 요소의 `ProjectTemplateLink` 특성은 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]가 이 프로젝트에 할당할 이름을 설정합니다. 특성이 없으면 `ProjectName` *.vstemplate* 파일의 이름이 프로젝트 이름으로 사용 됩니다.

```
<VSTemplate Version="3.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink ProjectName="My Windows Application">
                WindowsApp\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink ProjectName="My Class Library">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>참조
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [방법: 다중 프로젝트 템플릿 만들기](../ide/how-to-create-multi-project-templates.md)

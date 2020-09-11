---
title: ProjectTemplateLink 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e87b33d9b4b3863b89ecd06c3ea959c6e35ec7c0
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011985"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>ProjectTemplateLink 요소(Visual Studio 템플릿)
다중 프로젝트 템플릿에서 한 프로젝트의 *.vstemplate* 파일에 대 한 경로를 지정 합니다.

 \<VSTemplate> \<TemplateContent>
 \<ProjectCollection>
 \<ProjectTemplateLink>
디스크나 \<VSTemplate>
 \<TemplateContent>
 \<ProjectCollection>
 \<SolutionFolder>
 \<ProjectTemplateLink>

## <a name="syntax"></a>구문

```xml
<ProjectTemplateLink ProjectName="Name">
    PathToTemplateFile
</ProjectTemplateLink>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|`ProjectName`|선택적 특성입니다.<br /><br /> 다중 프로젝트 템플릿에 있는 개별 프로젝트 각각의 이름을 지정합니다. **새 프로젝트** 대화 상자는 개별 프로젝트에 이름을 할당할 수 없습니다.|
|`CopyParameters`|각 연결된 템플릿에 복사할 기본 그룹 템플릿에서 모든 변수를 활성화할수 있습니다.<br /><br /> 연결된 템플릿의 매개 변수에는 `"$ext_*$"` 접두사가 있습니다. 예를 들어 부모 그룹 템플릿에서 매개 변수에 `$projectname$` **ExampleProject1**값이 있는 경우 연결 된 템플릿이 실행 될 때 해당 매개 변수는 `$ext_projectname$` `$projectname$` 부모 그룹 템플릿의 매개 변수 복사본 인 매개 변수를 가져옵니다.<br /><br /> 그에 따라 연결된 템플릿을 통해 부모 그룹 템플릿에서만 편리하게 만들 수 있는 일부 공통 매개 변수를 공유할 수 있습니다.<br /><br /> 이 특성은 선택적이며 포함되지 않은 경우 기본값이 `false`로 자동 설정됩니다.<br /><br /> 이 특성은 Visual Studio 2013 업데이트 2에서 도입되었습니다. 올바른 제품 버전을 참조 하려면 [VISUAL STUDIO 2013 SDK 업데이트 2에서 제공 되는 참조 어셈블리](/previous-versions/dn632168(v=vs.120))를 참조 하세요.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|다중 프로젝트 템플릿의 구성과 내용을 지정합니다.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|다중 프로젝트 템플릿의 프로젝트를 그룹화합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

 이 텍스트는 템플릿의 *.vstemplate* 파일에 대 한 경로를 지정 합니다.

## <a name="remarks"></a>설명
 다중 프로젝트 템플릿은 두 개 이상의 프로젝트에 대한 컨테이너로 사용됩니다. `ProjectTemplateLink`요소는 템플릿의 프로젝트 중 하나에 대 한 *.vstemplate* 파일의 위치를 지정 하는 데 사용 됩니다. 다중 프로젝트 템플릿의 *.vstemplate* 파일은 `ProjectTemplateLink` 템플릿의 각 프로젝트에 대해 하나의 요소를 포함 합니다. 다중 프로젝트 템플릿에 대 한 자세한 내용은 [방법: 다중 프로젝트 템플릿 만들기](../ide/how-to-create-multi-project-templates.md)를 참조 하세요.

## <a name="example"></a>예
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
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">
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
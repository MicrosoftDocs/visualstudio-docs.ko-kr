---
title: 템플릿콘텐츠 요소(비주얼 스튜디오 템플릿) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent
helpviewer_keywords:
- TemplateContent element [Visual Studio project templates]
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 577ce71d3900947cde1de9a1e913124ab778a1ee
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699229"
---
# <a name="templatecontent-element-visual-studio-templates"></a>TemplateContent 요소(Visual Studio 템플릿)

템플릿의 내용을 지정합니다.

요소 계층 구조:

```xml
<VSTemplate>
  <TemplateContent>
```

## <a name="syntax"></a>구문

```xml
<TemplateContent>
    ...
</TemplateContent>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|[BuildOnLoad](../extensibility/buildonload-visual-studio-templates.md)|템플릿에서 프로젝트를 만들 때 솔루션을 빌드할지 여부를 지정합니다.|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> 다중 프로젝트 템플릿의 구성과 내용을 지정합니다.|
|[프로젝트](../extensibility/project-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> 프로젝트에 추가할 파일 또는 디렉터리를 지정합니다.|
|[참조](../extensibility/references-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> 항목 템플릿에 필요한 어셈블리 참조를 지정합니다.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|선택적 요소입니다.<br /><br /> 템플릿에 포함된 파일을 지정합니다.|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> 템플릿에서 프로젝트 또는 항목을 만들 때 사용할 사용자 지정 매개 변수를 지정합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|필수 요소입니다.<br /><br /> 프로젝트 템플릿, 항목 템플릿 또는 시작 키트에 대한 모든 메타데이터가 들어 있습니다.|

## <a name="remarks"></a>설명
 `TemplateContent`는 필수 요소입니다.

## <a name="example"></a>예제
 다음 예제에서는 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 응용 프로그램에 대 한 프로젝트 템플릿에 대 한 메타 데이터를 보여 합니다.

```xml
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
            <ProjectItem>Form1.cs</ProjectItem>
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
- [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)

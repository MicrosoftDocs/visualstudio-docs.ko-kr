---
title: CreateNewFolder 요소 (Visual Studio 템플릿) | Microsoft Docs
description: CreateNewFolder 요소에 대해 알아보고, 프로젝트가 생성 될 대상 디렉터리가 존재 하지 않는지 확인할 지 여부를 결정 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CreateNewFolder
helpviewer_keywords:
- CreateNewFolder element [Visual Studio project templates]
ms.assetid: acef2016-4140-45d6-ace8-b8160eabd676
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3c2d8da615c350fc53b81532972cef65f6cd6ed7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089474"
---
# <a name="createnewfolder-element-visual-studio-templates"></a>CreateNewFolder 요소 (Visual Studio 템플릿)
프로젝트를 만들 대상 디렉터리가 없음을 확인할지 여부를 결정합니다. 디렉터리가 있으면 프로젝트에 대해 새 디렉터리를 만들 수 있습니다. 일반적으로는 모든 공통 프로젝트 형식이 새 디렉터리에 새 프로젝트를 만들지 여부를 결정하는 데 사용하는 `NewProjectRequiresNewFolder(VsTemplate)` 레지스트리 플래그(`HKEY_LOCAL_MACHINE/SOFTWARE(/Wow6432Node)/Microsoft/VisualStudio/<version number>/Projects/<project GUID>`)가 이 설정을 재정의합니다.

 \<VSTemplate> \<TemplateData>
 \<CreateNewFolder>

## <a name="syntax"></a>구문

```
<CreateNewFolder>
    true/false
</CreateNewFolder>
```

## <a name="type"></a>형식
 `Boolean`

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 템플릿을 분류하고 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에서 템플릿이 표시되는 방식을 정의합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

 텍스트는 템플릿에서 프로젝트를 만들 때 새 컨테이너 폴더를 만들어야 하는지 여부를 나타내는 `true` 또는 `false`여야 합니다.

## <a name="remarks"></a>설명
 `CreateNewFolder`는 선택적 요소입니다. 기본값은 `true`입니다.

 `CreateNewFolder` 요소에 지정된 값은 기본 프로젝트 시스템에서 지원하는 경우 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서만 적용됩니다.

## <a name="example"></a>예제
 다음 코드 예제에서는 템플릿에서 프로젝트를 만들 때 새 폴더를 만들지 않도록 지정합니다.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <CreateNewFolder>false</CreateNewFolder>
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

## <a name="see-also"></a>참조
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)

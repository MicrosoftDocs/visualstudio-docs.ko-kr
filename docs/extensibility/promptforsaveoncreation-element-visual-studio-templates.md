---
title: PromptForSaveOnCreation 요소(Visual Studio 템플릿)
titleSuffix: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#PromptForSaveOnCreation
helpviewer_keywords:
- PromptForSaveOnCreation element [Visual Studio project templates]
ms.assetid: 75174674-0c3c-4b57-b2fd-6ea8e817b67d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: ffc610cf701bdf5be3a0b6116455ac413fbd6dcd
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743132"
---
# <a name="promptforsaveoncreation-element-visual-studio-templates"></a>PromptForSaveOnCreation 요소 (Visual Studio 템플릿)

프로젝트를 만들 때 **새 프로젝트** 대화 상자를 통해 프로젝트 저장 위치를 묻는 메시지를 사용자에 게 표시할지 여부를 지정 합니다. 이 요소를로 설정 하면 `true` 저장 위치를 묻는 메시지가 사용자에 게 표시 됩니다. 인 경우에는 `false` 메시지가 표시 되지 않습니다. 즉, 임시 프로젝트가 생성 됩니다.

```xml
\<VSTemplate>
\<TemplateData>
\<PromptForSaveOnCreation>
```

## <a name="syntax"></a>구문

```xml
<PromptForSaveOnCreation> true/false </PromptForSaveOnCreation>
```

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

 텍스트는 또는 여야 합니다 `true` `false` `true` . 즉, 새 프로젝트를 만들 때 저장 위치를 묻는 메시지가 사용자에 게 표시 됩니다.

## <a name="remarks"></a>설명
 `PromptForSaveOnCreation`는 선택적 요소입니다. 기본값은 `false`입니다.

 임시 프로젝트는 해당 프로젝트의 내용을 디스크에 저장 하지 않고 만들고 수정할 수 있는 프로젝트입니다.

## <a name="example"></a>예
 다음 예제에서는 `PromptForSaveOnCreation` `false` 프로젝트를 임시 프로젝트로 만들 수 있도록를 지정 하는 값을로 설정 합니다.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <PromptForSaveOnCreation>false</PromptForSaveOnCreation>
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

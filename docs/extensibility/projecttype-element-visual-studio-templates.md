---
title: 프로젝트 유형 요소(비주얼 스튜디오 템플릿) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d794bd5e81e77a892b5a3be38ff73ab805582dd7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701802"
---
# <a name="projecttype-element-visual-studio-templates"></a>ProjectType 요소(비주얼 스튜디오 템플릿)
**새** 프로젝트 또는 **새 항목 추가** 대화 상자에서 지정된 그룹 아래에 표시되도록 프로젝트 템플릿을 분류합니다.

> [!WARNING]
> 프로젝트 템플릿은 Visual Studio 2012에서 시작하여 C++에 지원됩니다. Visual Studio 2010 및 이전 버전에서는 C++에 대해 지원되지 않습니다.

 \<VS템플릿 \<> 템플릿데이터> \<프로젝트 유형>

## <a name="syntax"></a>구문

```xml
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|템플릿을 분류하고 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에서 템플릿이 표시되는 방식을 정의합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

 이 값은 템플릿이 만들 프로젝트 유형을 지정하며 다음 값 중 하나를 포함해야 합니다.

- `CSharp`: 템플릿이 프로젝트 또는 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 항목을 생성되도록 지정합니다.

- `VisualBasic`: 템플릿이 프로젝트 또는 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 항목을 생성되도록 지정합니다.

- `Web`: 템플릿이 웹 프로젝트 또는 항목을 만들수 있도록 지정합니다. `ProjectType` 요소에 이 값이 포함되어 있으면 프로젝트 또는 항목의 언어가 [ProjectSubType 요소(Visual Studio 템플릿)에 정의됩니다.](../extensibility/projectsubtype-element-visual-studio-templates.md)

## <a name="remarks"></a>설명
 `ProjectType`은 `TemplateData`의 필수 자식 요소입니다.

 요소값은 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에 템플릿이 있는 위치를 지정합니다. `ProjectType` 예를 들어 값이 있는 `ProjectType` 템플릿이 **새 프로젝트** 대화 상자의 **Visual C#** 노드 아래에 `CSharp` 나타납니다.

 [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) 요소를 사용하여 템플릿 하위 유형을 지정할 수 있습니다.

## <a name="example"></a>예제
 다음 예제에서는 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 응용 프로그램에 대 한 프로젝트 템플릿에 대 한 메타 데이터를 보여 합니다.

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
- [비주얼 스튜디오 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [프로젝트서브타입 요소(비주얼 스튜디오 템플릿)](../extensibility/projectsubtype-element-visual-studio-templates.md)

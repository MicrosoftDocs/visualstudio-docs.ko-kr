---
title: 프로젝트서브타입 요소(비주얼 스튜디오 템플릿) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 27396ad1bcc4e181b2b8cecd6ca863db2412630d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701827"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>프로젝트서브타입 요소(비주얼 스튜디오 템플릿)
템플릿을 `ProjectType` 요소에 지정된 값의 하위 범주로 분류합니다.

 \<VS템플릿 \<> 템플릿데이터> \<프로젝트서브타입>

## <a name="syntax"></a>구문

```xml
<ProjectSubType> SubType </ProjectSubType>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|필수 요소입니다.<br /><br /> 템플릿을 분류하고 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에서 템플릿이 표시되는 방식을 정의합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

 이 값은 템플릿의 하위 범주를 지정합니다.

## <a name="remarks"></a>설명
 `ProjectSubType`은 `TemplateData`의 선택적 자식 요소입니다.

 요소는 `ProjectSubType` [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) 요소에 하위 범주를 제공합니다. 이 값에는 다음이 포함될 수 있습니다.

- `SmartDevice-NETCFv1`: 템플릿이 버전 1.0을 대상으로 지정합니다. [!INCLUDE[Compact](../extensibility/includes/compact_md.md)]

- `SmartDevice-NETCFv2`: 템플릿이 버전 2.0을 대상으로 지정합니다. [!INCLUDE[Compact](../extensibility/includes/compact_md.md)]

  템플릿에 값이 `ProjectType` `Web`있는 요소가 포함된 경우 `ProjectSubType` 요소는 템플릿의 프로그래밍 언어를 지정합니다. 이 요소에는 다음 값이 있을 수 있습니다.

- `CSharp`: 템플릿이 웹 프로젝트 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 또는 항목을 만들수 있도록 지정합니다.

- `VisualBasic`: 템플릿이 웹 프로젝트 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 또는 항목을 만들수 있도록 지정합니다.

## <a name="example"></a>예제
 다음 예제에서는 버전 2.0을 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 대상으로 하는 [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] 장치 응용 프로그램에 대 한 프로젝트 템플릿에 대 한 메타 데이터를 보여 주다.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic device template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>
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
- [비주얼 스튜디오 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [ProjectType 요소(비주얼 스튜디오 템플릿)](../extensibility/projecttype-element-visual-studio-templates.md)

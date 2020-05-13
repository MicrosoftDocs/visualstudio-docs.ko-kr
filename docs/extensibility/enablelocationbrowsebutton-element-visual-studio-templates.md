---
title: 인에이블위치브라우시볼 버튼 요소(비주얼 스튜디오 템플릿) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#EnableLocationBrowseButton
helpviewer_keywords:
- EnableLocationBrowseButton [Visual Studio project templates]
ms.assetid: a12d10d8-af49-482a-af77-e084fd07a47d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 263157d5c6fefc208f28caa55475ba329a0d230f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711984"
---
# <a name="enablelocationbrowsebutton-element-visual-studio-templates"></a>사용 위치찾아보기 단추 요소(비주얼 스튜디오 템플릿)
**새 프로젝트** 대화 상자에서 **찾아보기** 단추를 사용할 수 있는지 여부를 지정하여 사용자가 새 프로젝트가 저장된 기본 디렉터리를 쉽게 수정할 수 있도록 합니다.

 \<VS템플릿 \<> 템플릿데이터> \<인에이블위치찾아보기버튼>

## <a name="syntax"></a>구문

```
<EnableLocationBrowseButton> true/false </EnableLocationBrowseButton>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

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

 새 프로젝트 대화 `true` `false`상자에 **찾아보기** 단추를 표시할지 여부를 **New Project** 나타내는 텍스트 또는 이중 하나여야 합니다.

## <a name="remarks"></a>설명
 `EnableLocationBrowseButton`는 선택적 요소입니다. 기본값은 `true` **새 프로젝트** 대화 상자에 **찾아보기** 단추를 표시하는 입니다.

 새 **프로젝트** 대화 상자에서 **위치** 텍스트 상자에새 프로젝트가 저장되는 디렉터리를 지정합니다. **찾아보기** 단추를 사용하면 컴퓨터에서 사용할 수 있는 다른 디렉터리로 쉽게 이동한 다음 새 프로젝트가 저장된 디렉터리로 선택할 수 있는 **프로젝트 위치** 대화 상자를 표시하여 이 디렉토리를 수정할 수 있습니다.

## <a name="example"></a>예제
 다음 예제에서는 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Windows 응용 프로그램에 대 한 메타 데이터를 보여 줍니다.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>
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

---
title: 위치필드 요소(비주얼 스튜디오 프로젝트 템플릿) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d993e84bec41486ef4dce6ad98c61f23ab2a46bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702879"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>위치필드 요소(비주얼 스튜디오 프로젝트 템플릿)
**새 프로젝트** 대화 상자의 **위치** 텍스트 상자가 프로젝트 템플릿에 대해 활성화, 사용 안 함 또는 숨겨져 있는지 여부를 지정합니다.

 \<VS템플릿 \<> 위치필드>> \<템플릿데이터 데이터

## <a name="syntax"></a>구문

```
<LocationField> Enabled/Disabled/Hidden </LocationField>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|필수 요소입니다.<br /><br /> 템플릿을 분류하고 **새 프로젝트**에 표시되는 방법을 정의합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

 유효한 텍스트 값은 다음과 같습니다.

- `Enabled`새 **프로젝트** 대화 상자의 **위치** 상자가 활성화되어 있음을 지정합니다.

- `Disabled`새 **프로젝트** 대화 상자의 **위치** 상자를 사용하지 않도록 지정합니다.

- `Hidden`새 **프로젝트** 대화 상자의 **위치** 상자가 숨김을 지정합니다.

## <a name="remarks"></a>설명
 기본값은 `Enabled`입니다.

 **새 프로젝트** 대화 상자의 **위치** 텍스트 상자를 사용하면 새 프로젝트가 저장되는 기본 디렉터리를 변경할 수 있습니다.

 `Location` 요소에 지정된 값은 기본 프로젝트 시스템이 지원하는 경우에만 대화 상자에서 적용됩니다.

## <a name="example"></a>예제
 다음 예제에서는 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 템플릿의 메타데이터를 보여 줍니다.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <LocationField>Disabled</LocationField>
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

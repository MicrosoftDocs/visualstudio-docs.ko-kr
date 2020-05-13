---
title: 어셈블리 요소(비주얼 스튜디오 템플릿 마법사 확장) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio Template Wizard Extension]
- <Assembly> element [Visual Studio Template Wizard Extension]
ms.assetid: 0c3dc280-1753-4ea2-a13c-d31d13b935b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 43f5adb8abc17f0509fb58263f307e5051af85dc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740068"
---
# <a name="assembly-element-visual-studio-template-wizard-extension"></a>어셈블리 요소(비주얼 스튜디오 템플릿 마법사 확장)
`IWizard` 인터페이스를 구현하는 어셈블리의 이름이나 강력한 이름을 지정합니다.

 \<VS템플릿 \<> 마법사확장> \<어셈블리>

## <a name="syntax"></a>구문

```
<Assembly>AssemblyName</Assembly>
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
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|템플릿 마법사를 사용자 지정하기 위한 등록 요소가 포함되어 있습니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

 이 텍스트는 인터페이스를 구현하는 어셈블리를 `IWizard` 지정합니다. 이 어셈블리 이름은 전체 어셈블리 이름으로 지정해야 합니다. `MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11dd0a3a, Custom = null`)을 입력합니다.

## <a name="remarks"></a>설명
 `Assembly`은 `WizardExtension`의 필수 자식 요소입니다.

## <a name="example"></a>예제
 다음 예제에서는 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Windows 응용 프로그램에 대 한 표준 프로젝트 템플릿에 대 한 메타 데이터를 보여 줍니다.

```xml
<VSTemplate Version="3.0.0" Type="Item"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyTemplate</Name>
        <Description>Template using IWizard extension</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
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
    <WizardExtension>
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11dd0a3a, Custom=null</Assembly>
        <FullClassName>MyWizard.CustomWizard</FullClassName>
    </WizardExtension>
</VSTemplate>
```

## <a name="see-also"></a>참조

- [비주얼 스튜디오 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [방법: 프로젝트 템플릿을 사용하여 마법사 사용](../extensibility/how-to-use-wizards-with-project-templates.md)

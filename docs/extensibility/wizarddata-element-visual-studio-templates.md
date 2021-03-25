---
title: WizardData 요소 (Visual Studio 템플릿) | Microsoft Docs
description: WizardData 요소 및이 요소에서 사용자 지정 XML을 지정 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardData
helpviewer_keywords:
- WizardData element [Visual Studio Templates]
- <WizardData> element [Visual Studio Templates]
ms.assetid: d0403a16-5d07-4fe5-b474-19ae3d9fd3ab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bd7b85433b4e02491852589d32eea9a4f223da14
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061890"
---
# <a name="wizarddata-element-visual-studio-templates"></a>WizardData 요소(Visual Studio 템플릿)

사용자 지정 XML을 지정 합니다.

```xml
\<VSTemplate>
\<WizardData>
```

## <a name="syntax"></a>구문

```xml
<WizardData>
    <!-- XML to pass to the custom wizard extension -->
    ...
</WizardData>
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
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 프로젝트 템플릿, 항목 템플릿 또는 시작 키트에 대 한 모든 메타 데이터를 포함 합니다.|

## <a name="text-value"></a>텍스트 값

텍스트 값은 선택적입니다.

이 텍스트는 [WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md) 요소에 지정 된 사용자 지정 마법사 확장에 전달할 사용자 지정 XML을 지정 합니다.

## <a name="remarks"></a>설명

이 요소에는 모든 XML을 지정할 수 있습니다. XML은 사용자 지정 마법사 확장에 매개 변수로 전달 되므로 확장에서이 요소의 콘텐츠를 사용할 수 있습니다. 이 데이터에 대 한 유효성 검사가 수행 되지 않습니다.

**Wizarddata** 요소의 콘텐츠는 메서드에 있는 매개 변수의 문자열 사전 내에 매개 변수로 전달 되 고 변경 되지 않은 상태로 전달 됩니다 `IWizard.RunStarted` . 사전 키의 이름은 `$wizarddata$` 입니다.

## <a name="example"></a>예제

다음 예제에서는 c # Windows 응용 프로그램에 대 한 표준 프로젝트 템플릿에 대 한 메타 데이터를 보여 줍니다.

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
    <WizardExtension>
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>
        <FullClassName>MyWizard.CustomWizard</FullClassName>
    </WizardExtension>
    <WizardData>
        <!-- XML to pass to the custom wizard extension -->
    </WizardData>
</VSTemplate>
```

## <a name="see-also"></a>참조

- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [WizardExtension 요소(Visual Studio 템플릿)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [방법: 프로젝트 템플릿에 마법사 사용](../extensibility/how-to-use-wizards-with-project-templates.md)

---
title: VS템플릿 요소(비주얼 스튜디오 템플릿) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords:
- VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 651e8b6dbbe11c450b105f3185e7e987bb30da9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697861"
---
# <a name="vstemplate-element-visual-studio-templates"></a>VS템플릿 요소(비주얼 스튜디오 템플릿)
프로젝트 템플릿, 항목 템플릿 또는 시작 키트에 대한 모든 메타데이터가 포함되어 있습니다.

## <a name="syntax"></a>구문

```csharp
<VSTemplate Type="TemplateType" Version="x.x.x">
    <TemplateData>    </TemplateData>
    <TemplateContent>    </TemplateContent>
    ...
</VSTemplate>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

| attribute | 설명 |
|-----------| - |
| `Type` | 템플릿을 프로젝트 템플릿 또는 항목 템플릿으로 식별합니다. 이 특성은 `Project` 또는 `Item`의 값을 가질 수 있습니다. |
| `Version` | 템플릿의 버전 번호를 지정합니다. 템플릿의 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] `Version` 속성 값이 `3.0.0`있습니다. |

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|필수 요소입니다.<br /><br /> 템플릿을 분류하는 데이터를 지정하고 **새 프로젝트** 또는 새 **항목 추가** 대화 상자에 표시되는 방법을 정의합니다.|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|필수 요소입니다.<br /><br /> 템플릿의 내용을 지정합니다.|
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|선택적 요소입니다.|
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|선택적 요소입니다.|

### <a name="parent-elements"></a>부모 요소
 없음

## <a name="remarks"></a>설명
 요소는 `VSTemplate` *.vstemplate* 파일의 루트 요소입니다.

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
- [비주얼 스튜디오 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)

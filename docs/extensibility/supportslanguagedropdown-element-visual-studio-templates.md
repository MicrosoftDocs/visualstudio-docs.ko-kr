---
title: SupportsLanguageDropDown 요소(Visual Studio 템플릿)
titleSuffix: ''
description: SupportsLanguageDropDown 요소 및 웹 항목 템플릿이 여러 언어에 대해 동일한 지 여부 및 언어 옵션을 사용할 수 있는지 여부를 지정 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 67bf92c8c447faac2969bde3f208823158663712
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056079"
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>SupportsLanguageDropDown 요소(Visual Studio 템플릿)

웹 항목 템플릿이 여러 언어에 대해 동일한 지 여부 및 **새 항목 추가** 대화 상자에서 **언어** 옵션을 사용할 수 있는지 여부를 지정 합니다.

 \<VSTemplate> \<TemplateData>
 \<SupportsLanguageDropDown>

## <a name="syntax"></a>구문

```xml
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>
```

## <a name="attributes-and-elements"></a>특성 및 요소

 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

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

 텍스트는 `true` `false` **새 항목 추가** 대화 상자에서 **언어** 옵션을 사용할 수 있는지 여부를 나타내는 또는 중 하나 여야 합니다.

## <a name="remarks"></a>설명

 `SupportsLanguageDropDown`는 선택적 요소입니다. 기본값은 `false`입니다.

 `SupportsLanguageDropDown`요소는 웹 항목 템플릿에만 사용할 수 있습니다.

 이 요소의 값을로 설정 하면 `true` 모든 프로그래밍 언어에 대해 항목 템플릿이 동일 하 고 **새 항목 추가** 대화 상자에서 **언어** 옵션을 사용할 수 있습니다. 이 옵션을 사용 하면 템플릿에서 만들려는 새 항목의 프로그래밍 언어를 선택할 수 있습니다.

## <a name="example"></a>예제

 다음 예에서는 **언어** 드롭다운 옵션을 표시 하도록를 지정 합니다.

```xml
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsLanguageDropDown>true</SupportsLanguageDropDown>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>참조

- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)

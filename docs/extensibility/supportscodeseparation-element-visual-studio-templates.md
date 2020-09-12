---
title: SupportsCodeSeparation 요소(Visual Studio 템플릿)
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation
helpviewer_keywords:
- SupportsCodeSeparation element [Visual Studio Templates]
- <SupportsCodeSeparation> element [Visual Studio Templates]
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4dfdf3244d09c5f3418c5403a32570c382c5365c
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038467"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>SupportsCodeSeparation 요소(Visual Studio 템플릿)
**새 항목 추가** 대화 상자에서 **별도의 파일에 코드 입력** 확인란을 사용할지 여부를 지정 합니다.

 \<VSTemplate> \<TemplateData>
 \<SupportsCodeSeparation>

## <a name="syntax"></a>구문

```
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 템플릿을 분류 하 고 **새 프로젝트** 또는 **새 항목** 대화 상자에 표시 되는 방법을 정의 합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

 텍스트는 `true` `false` **새 항목 추가** 대화 상자에서 **별도의 파일에 코드 입력** 확인란을 사용할 수 있는지 여부를 나타내는 또는 여야 합니다.

## <a name="remarks"></a>설명
 `SupportsCodeSeparation`는 선택적 요소입니다. 기본값은 `false`입니다.

 `SupportsCodeSeparation`요소는 웹 항목 템플릿에만 사용할 수 있습니다.

 코드 분리 또는 코드를 사용 하는 페이지 모델을 사용 하면 태그를 한 파일에 유지 하 고 프로그래밍 코드를 다른 파일에 유지할 수 있습니다. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 및 기타 .NET 언어는이 모델을 사용 합니다.

## <a name="example"></a>예제
 다음 예에서는 **별도의 파일에 코드 입력** 옵션을 표시 하도록 지정 합니다.

```
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsCodeSeparation>true</SupportsCodeSeparation>
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

## <a name="see-also"></a>참고 항목
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)

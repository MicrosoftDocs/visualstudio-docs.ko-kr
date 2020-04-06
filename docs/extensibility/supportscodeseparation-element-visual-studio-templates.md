---
title: 지원코드분리 요소(비주얼 스튜디오 템플릿) | 마이크로 소프트 문서
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
ms.openlocfilehash: bd52ae47f47f3ca1fce23f7cf8d37260ec86fb0c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699505"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>SupportsCodeSeparation 요소(Visual Studio 템플릿)
새 **항목 추가** 대화 **상자에서 별도의 파일** 의 배치 코드가 활성화되어 있는지 여부를 지정합니다.

 \<VS템플릿 \<> 템플릿데이터> \<지원코드분리>

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

|요소|Description|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|필수 요소입니다.<br /><br /> 템플릿을 분류하고 **새 프로젝트** 또는 **새 항목** 대화 상자에 표시되는 방법을 정의합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

 텍스트는 새 `true` 항목 `false` **추가** 대화 **상자에서 별도의 파일** 의 배치 코드가 활성화되어 있는지 여부를 나타내는 또는 이중 하나여야 합니다.

## <a name="remarks"></a>설명
 `SupportsCodeSeparation`는 선택적 요소입니다. 기본값은 `false`입니다.

 이 `SupportsCodeSeparation` 요소는 웹 항목 템플릿에서만 사용할 수 있습니다.

 코드 분리 또는 코드 뒤 페이지 모델을 사용하면 태그가 한 파일에 있고 다른 파일의 프로그래밍 코드를 유지할 수 있습니다. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]및 기타 .NET 언어는 이 모델을 사용합니다.

## <a name="example"></a>예제
 다음 예제에서는 별도의 파일 **옵션에 배치 코드를** 표시하도록 지정합니다.

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

## <a name="see-also"></a>참조
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)

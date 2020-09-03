---
title: ProvideDefaultName 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 192716198f605a5f6b4f62730e84dcf83b4229cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701712"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>ProvideDefaultName 요소 (Visual Studio 템플릿)
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]프로젝트 시스템이 **새 항목 추가** 또는 **새 프로젝트** 대화 상자에서 템플릿의 기본 이름을 생성할지 여부를 지정 합니다.

 \<VSTemplate> \<TemplateData>
 \<ProvideDefaultName>

## <a name="syntax"></a>구문

```xml
<ProvideDefaultName> true/false </ProvideDefaultName>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

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

 텍스트는 또는 중 하나 여야 합니다 `true` `false` . **새 항목 추가** 또는 **새 프로젝트** 대화 상자에서 템플릿의 기본 이름을 생성할지 여부를 나타냅니다.

## <a name="remarks"></a>설명
 `ProvideDefaultName`는 선택적 요소입니다. 기본값은 `true`입니다.

 요소가 이면 `ProvideDefaultName` `false` **새 항목 추가** 및 **새 프로젝트** 대화 상자의 **이름** 상자에 값이 포함 `<Enter_name>` 됩니다.

 [Defaultname](../extensibility/defaultname-element-visual-studio-templates.md) 요소를 사용 하 여 **새 항목 추가** 및 **새 프로젝트** 대화 상자에서 프로젝트 또는 항목의 기본 이름을 지정 합니다. `ProvideDefaultName`요소의 값이 인 경우 `true` 프로젝트의 요소를 생략 하면 `DefaultName` 대화 상자에 템플릿 이름, 즉 [name](../extensibility/name-element-visual-studio-templates.md) 요소의 값이 채워집니다.

## <a name="example"></a>예제
 다음 코드 예제에서는 요소를 `ProvideDefaultName` 로 설정 합니다 `false` .

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProvideDefaultName>false</ProvideDefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>참조
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)

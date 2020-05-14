---
title: 맥스 프레임 워크 버전 요소 (비주얼 스튜디오 템플릿) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c3acf9c40499417fe180ce470224824cc89a113
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702628"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>맥스 프레임 워크 버전 요소 (비주얼 스튜디오 템플릿)

템플릿에 필요한 .NET 프레임워크의 최대 버전을 지정합니다. **새 프로젝트** 대화 상자의 **대상 프레임워크 버전** 드롭다운에서 사용할 수 있는 가장 높은 값을 결정합니다. 사용자가 프레임워크 버전을 선택할 수 있도록 하려면 [필수 FrameworkVersion을](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) 템플릿의 최소 .NET 프레임워크 버전으로 지정해야 합니다.

> [!IMPORTANT]
> Visual Studio 2017 버전 15.6에서 시작하여 **대상 프레임워크 버전** 드롭다운은 더 이상 새 **프로젝트** 대화 상자의 **템플릿** 섹션에 표시된 템플릿에 대한 필터가 아닙니다. 대신 **대상 프레임워크 버전** 드롭다운은 선택한 템플릿에 대한 프레임워크 선택으로 작동합니다.

 \<VS템플릿 \<> 템플릿데이터> \<맥스프레임워크버전>

## <a name="syntax"></a>구문

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|필수 요소입니다.<br /><br /> 템플릿을 분류하고 **새 프로젝트** 또는 새 **항목 추가** 대화 상자에 표시되는 방법을 정의합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

 텍스트는 템플릿에서 허용하는 .NET Framework의 가장 높은 버전 번호여야 합니다.

## <a name="remarks"></a>설명

`MaxFrameworkVersion`는 선택적 요소입니다. 템플릿에 `MaxFrameworkVersion` 대한 .NET Framework 버전의 지원되는 범위를 실수로 제한하지 않도록 필요한 경우가 아니면 요소를 생략해야 합니다. .NET Framework가 템플릿에 적용되지 않는 경우에도 생략해야 합니다.

## <a name="example"></a>예제

다음 예제에서는 표준 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 클래스 템플릿에 대한 메타데이터를 보여 줍니다.

```xml
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>3.0</RequiredFrameworkVersion>
        <MaxFrameworkVersion>4.7.1</MaxFrameworkVersion>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

이 예제에서 `MaxFrameworkVersion`.NET Framework의 최대 버전은 으로 표시되는 템플릿에 필요한 값입니다. 이 템플릿으로 만든 프로젝트는 최대 4.7.1.NET Framework 버전을 대상으로 할 수 있습니다.

## <a name="see-also"></a>참조

- [비주얼 스튜디오 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)

---
title: MaxFrameworkVersion 요소 (Visual Studio 템플릿) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702628"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion 요소 (Visual Studio 템플릿)

템플릿에 필요한 .NET Framework의 최대 버전을 지정 합니다. **새 프로젝트** 대화 상자의 **대상 프레임 워크 버전** 드롭다운에서 사용할 수 있는 가장 높은 값을 결정 합니다. 사용자가 프레임 워크 버전을 선택할 수 있으려면 템플릿의 최소 .NET Framework 버전으로 [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) 도 지정 해야 합니다.

> [!IMPORTANT]
> Visual Studio 2017 버전 15.6부터 **대상 프레임 워크 버전** 드롭다운은 더 이상 **새 프로젝트** 대화 상자의 **템플릿** 섹션에 표시 된 템플릿에 대 한 필터가 아닙니다. 대신 **대상 프레임 워크 버전** 드롭다운은 선택한 템플릿에 대 한 프레임 워크 선택기로 작동 합니다.

 \<VSTemplate> \<TemplateData>
 \<MaxFrameworkVersion>

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

|요소|설명|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 템플릿을 분류 하 고 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에 템플릿을 표시 하는 방법을 정의 합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

 텍스트는 템플릿에서 허용 하는 .NET Framework의 가장 높은 버전 번호 여야 합니다.

## <a name="remarks"></a>설명

`MaxFrameworkVersion`는 선택적 요소입니다. `MaxFrameworkVersion`요소는 필요 하지 않은 경우 생략 해야 합니다. 따라서 템플릿에 대해 지원 되는 .NET Framework 버전의 범위를 실수로 제한 하지 않습니다. .NET Framework 템플릿에 적용 되지 않는 경우에도 생략 해야 합니다.

## <a name="example"></a>예

다음 예제에서는 표준 클래스 템플릿에 대 한 메타 데이터를 보여 줍니다 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

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

이 예제에서는에 의해 표현 되는 템플릿에 필요한 .NET Framework의 최대 버전 `MaxFrameworkVersion` 은 4.7.1입니다. 이 템플릿을 사용 하 여 만든 프로젝트는 최대 4.7.1 .NET Framework 버전을 대상으로 지정할 수 있습니다.

## <a name="see-also"></a>참조

- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)

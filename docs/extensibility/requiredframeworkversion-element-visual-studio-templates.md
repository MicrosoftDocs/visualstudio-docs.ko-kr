---
title: RequiredFrameworkVersion 요소(Visual Studio 템플릿)
titleSuffix: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ce8a342f7b3582fb8b2b3839a44e545071b7177
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89741693"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>RequiredFrameworkVersion 요소 (Visual Studio 템플릿)

템플릿에 필요한 .NET Framework의 최소 버전을 지정 합니다. 그러면 **대상 프레임 워크 버전** 드롭다운이 **새 프로젝트** 대화 상자에 표시 됩니다. `RequiredFrameworkVersion`또한 요소는 드롭다운에서 사용할 수 있는 가장 낮은 값을 결정 합니다.

> [!IMPORTANT]
> Visual Studio 2017 버전 15.6부터 **대상 프레임 워크 버전** 드롭다운은 더 이상 **새 프로젝트** 대화 상자의 **템플릿** 섹션에 표시 된 템플릿에 대 한 필터가 아닙니다. 대신 드롭다운이 선택 된 템플릿에 대 한 프레임 워크 선택기로 작동 합니다.

 \<VSTemplate> \<TemplateData>
 \<RequiredFrameworkVersion>

## <a name="syntax"></a>구문

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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

 텍스트는 템플릿에 필요한 .NET Framework의 최소 버전 번호 여야 합니다.

## <a name="remarks"></a>설명

`RequiredFrameworkVersion`는 선택적 요소입니다. 템플릿이 .NET Framework의 특정 최소 버전 (및 이후 버전)을 지 원하는 경우에만이 요소를 사용 합니다. 요소를 지정 하 `RequiredFrameworkVersion` 고 템플릿이 .NET Framework의 특정 최소 버전을 지원 하지 않는 경우 **대상 프레임 워크 버전** 드롭다운에 해당 사항이 없으면이 표시 됩니다.

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

이 예제에서로 표시 되는 템플릿에 필요한 .NET Framework의 최소 버전 `RequiredFrameworkVersion` 은 3.0입니다. 이 템플릿을 사용 하 여 만든 프로젝트는 3.0에서 시작 하는 .NET Framework 버전을 대상으로 지정할 수 있습니다.

## <a name="see-also"></a>참조

- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [Framework 대상 지정 개요](../ide/visual-studio-multi-targeting-overview.md)

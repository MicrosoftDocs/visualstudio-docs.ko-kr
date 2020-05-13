---
title: 필수프레임워크버전 요소(비주얼 스튜디오 템플릿) | 마이크로 소프트 문서
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
ms.openlocfilehash: 060ebc0633de67d93257e24c2dff24d2aa0970da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701506"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>필수프레임워크버전 요소(비주얼 스튜디오 템플릿)

템플릿에 필요한 .NET 프레임워크의 최소 버전을 지정합니다. **대상 프레임워크 버전** 드롭다운이 새 **프로젝트** 대화 상자에 표시됩니다. `RequiredFrameworkVersion` 또한 요소는 드롭다운에서 사용할 수 있는 가장 낮은 값을 결정합니다.

> [!IMPORTANT]
> Visual Studio 2017 버전 15.6에서 시작하여 **대상 프레임워크 버전** 드롭다운은 더 이상 새 **프로젝트** 대화 상자의 **템플릿** 섹션에 표시된 템플릿에 대한 필터가 아닙니다. 대신 드롭다운은 선택한 템플릿에 대한 프레임워크 선택기역할을 합니다.

 \<VS템플릿 \<> 템플릿데이터> \<필수프레임 워크>

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

|요소|Description|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|필수 요소입니다.<br /><br /> 템플릿을 분류하고 **새 프로젝트** 또는 새 **항목 추가** 대화 상자에 표시되는 방법을 정의합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

 텍스트는 템플릿에 필요한 .NET Framework의 최소 버전 번호여야 합니다.

## <a name="remarks"></a>설명

`RequiredFrameworkVersion`는 선택적 요소입니다. 템플릿이 .NET Framework의 특정 최소 버전(및 이후 버전인 경우)을 지원하는 경우에만 이 요소를 사용합니다. 요소를 지정하고 템플릿이 .NET Framework의 특정 최소 버전을 지원하지 않는 경우 **대상 프레임워크 버전** 드롭다운이 적용되지 않을 때 표시됩니다. `RequiredFrameworkVersion`

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

이 예제에서는 `RequiredFrameworkVersion`에서 로 표시되는 템플릿에 필요한 .NET Framework의 최소 버전은 3.0입니다. 이 템플릿으로 만든 프로젝트는 3.0부터 .NET Framework 버전을 대상으로 할 수 있습니다.

## <a name="see-also"></a>참조

- [비주얼 스튜디오 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [Framework 대상 지정 개요](../ide/visual-studio-multi-targeting-overview.md)

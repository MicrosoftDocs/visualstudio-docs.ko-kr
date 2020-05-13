---
title: 정렬 순서 요소(비주얼 스튜디오 템플릿) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 935d00335a21d3e129e79ce351e554ea93787447
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699965"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder 요소(Visual Studio 템플릿)
**새 프로젝트** 또는 **새 항목 추가** 대화 상자에 나타나는 것과 같이 동일한 범주의 다른 템플릿 중에서 템플릿을 정렬하는 데 사용되는 값을 지정합니다.

 \<VS템플릿 \<> 템플릿데이터> \<정렬 순서>

## <a name="syntax"></a>구문

```
<SortOrder> ... </SortOrder>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|필수 요소입니다.<br /><br /> 템플릿을 분류하고 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에서 템플릿이 표시되는 방식을 정의합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

 정렬 `integer` 순서 값을 나타내는 A입니다.

## <a name="remarks"></a>설명
 `SortOrder`는 선택적 요소입니다. 기본값은 100이고 모든 값은 10의 배수여야 합니다.

 사용자가 `SortOrder` 만든 템플릿에 대해 요소는 무시됩니다. 사용자가 만든 모든 템플릿은 사전순으로 정렬됩니다.

 정렬 순서 값이 낮은 템플릿은 정렬 순서 값이 높은 템플릿 앞에 **새 프로젝트** 또는 새 **항목 추가** 대화 상자에 나타납니다.

## <a name="example"></a>예제
 다음 예제에서는 표준 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 클래스 템플릿에 대한 메타데이터를 보여 줍니다.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>290</SortOrder>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

 이 예제에서는 `SortOrder` 요소가 상대적으로 높습니다. 다른 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 항목 템플릿의 `SortOrder` 값이 새 `290` **항목** 대화 상자의 이 템플릿 앞에 표시될 가능성이 높습니다.

## <a name="see-also"></a>참조
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)

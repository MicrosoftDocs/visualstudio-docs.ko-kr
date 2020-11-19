---
title: Reference 요소 (Visual Studio 템플릿) | Microsoft Docs
description: 참조 요소 및 프로젝트에 항목이 추가 될 때 추가할 어셈블리 참조를 지정 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcb713a62ebc9a0c3e4daf5aa16f36779b1a1fdc
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903769"
---
# <a name="reference-element-visual-studio-templates"></a>Reference 요소 (Visual Studio 템플릿)
항목이 프로젝트에 추가될 때 추가할 어셈블리 참조를 지정합니다.

 \<VSTemplate> \<TemplateContent>
 \<References>
 \<Reference>

## <a name="syntax"></a>구문

```xml
<Reference>
    <Assembly> ... </Assembly>
</Reference>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[어셈블리](../extensibility/assembly-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 템플릿에서 해당 어셈블리의 참조를 프로젝트에 추가 하는 데 사용 하는 어셈블리에 대 한 정보를 지정 합니다. `Assembly`모든 요소에는 요소가 하나 있어야 합니다 `Reference` .|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[참조](../extensibility/references-element-visual-studio-templates.md)|템플릿이 프로젝트에 추가 하는 어셈블리 참조를 그룹화 합니다.|

## <a name="remarks"></a>설명
 `Reference`은 `References`의 필수 자식 요소입니다.

 `Reference`및 `References` 요소는 특성 값이 인 *.vstemplate* 파일에만 사용할 수 있습니다 `Type` `Item` .

## <a name="example"></a>예
 다음 예제에서는 `TemplateContent` 항목 템플릿의 요소를 보여 줍니다. 이 XML은 *System.dll* 및 *System.Data.dll* 어셈블리에 대 한 참조를 추가 합니다.

```xml
<TemplateContent>
    <References>
        <Reference>
            <Assembly>
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
        <Reference>
            <Assembly>
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
    </References>
    ...
</TemplateContent>
```

## <a name="see-also"></a>참조
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)

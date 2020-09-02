---
title: Assembly 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c80044657b16448ba4567fff839274226985fa14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80740038"
---
# <a name="assembly-element-visual-studio-templates"></a>Assembly 요소 (Visual Studio 템플릿)
템플릿에서 해당 어셈블리의 참조를 프로젝트에 추가 하는 데 사용 하는 어셈블리에 대 한 정보를 지정 합니다.

 \<VSTemplate> \<TemplateContent>
 \<References>
 \<Reference>
 \<Assembly>

## <a name="syntax"></a>구문

```
<Assembly> AssemblyName </Assembly>
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
|[참조](../extensibility/reference-element-visual-studio-templates.md)|항목이 프로젝트에 추가될 때 추가할 어셈블리 참조를 지정합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

 이 텍스트는 항목 템플릿이 인스턴스화될 때 프로젝트에 추가할 어셈블리를 지정 합니다. 이 어셈블리 이름은 다음 방법 중 하나로 지정 해야 합니다.

- 전체 어셈블리 이름으로 예:

    ```
    <Assembly>
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.
    </Assembly>
    ```

- 단순 텍스트 참조로. 다음은 그 예입니다.

    ```
    <Assembly> System </Assembly>
    ```

## <a name="remarks"></a>설명
 `Assembly`은 `Reference`의 필수 자식 요소입니다.

 `Reference`, `References,` 및 요소는 `Assembly` 특성 값이 인 *.vstemplate* 파일에만 사용할 수 있습니다 `Type` `Item` .

## <a name="example"></a>예제
 다음 예제에서는 `TemplateContent` 항목 템플릿의 요소를 보여 줍니다. 이 XML은 *System.dll* 및 *System.Data.dll* 어셈블리에 대 한 참조를 추가 합니다.

```
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

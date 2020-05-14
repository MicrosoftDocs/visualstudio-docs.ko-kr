---
title: 참조 요소(비주얼 스튜디오 템플릿) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef31c5e7550ec7c6e4570d156d364afcf4ad6819
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701609"
---
# <a name="references-element-visual-studio-templates"></a>참조 요소(비주얼 스튜디오 템플릿)
템플릿이 프로젝트에 추가하는 어셈블리 참조를 그룹합니다.

 \<VS템플릿 \<> 템플릿콘텐츠> \<참조>

## <a name="syntax"></a>구문

```xml
<References>
    <Reference>... </Reference>
    <Reference>... </Reference>
    ...
</References>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|[참조](../extensibility/reference-element-visual-studio-templates.md)|필수 요소입니다.<br /><br /> 항목이 프로젝트에 추가될 때 추가할 어셈블리 참조를 지정합니다. `References` 요소에 하나 이상의 `Reference` 요소가 있어야 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|템플릿의 내용을 지정합니다.|

## <a name="remarks"></a>설명
 `References`은 `TemplateContent`의 선택적 자식 요소입니다.

 `Reference` 및 `References` 요소는 `Type` 의 특성 값이 있는 *.vstemplate* 파일에서만 사용할 수 `Item`있습니다.

## <a name="example"></a>예제
 다음 예제에서는 항목 `TemplateContent` 템플릿의 요소를 보여 줍니다. 이 XML은 *System.dll* 및 *System.Data.dll* 어셈블리에 대한 참조를 추가합니다.

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
- [비주얼 스튜디오 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)

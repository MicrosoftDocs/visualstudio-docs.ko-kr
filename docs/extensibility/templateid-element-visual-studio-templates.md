---
title: 템플릿 ID 요소(비주얼 스튜디오 템플릿) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8eb5abac9c837b3022354d6da743ac8f21d5e41d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699063"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID 요소(Visual Studio 템플릿)
[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) 요소에 의해 항목 템플릿 그룹으로 분류되는 항목 템플릿에 대한 식별자를 지정합니다.

 \<VS템플릿 \<> 템플릿데이터> \<템플릿ID>

## <a name="syntax"></a>구문

```
<TemplateID> ... </TemplateID>
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
 요소별로 항목 템플릿 그룹으로 분류되는 항목 템플릿의 식별자를 나타내는 A입니다. `string` `TemplateGroupID`

## <a name="remarks"></a>설명
 `TemplateID`는 선택적 요소입니다.

 .vstemplate 파일이 `TemplateID` 요소를 생략하면 [Name](../extensibility/name-element-visual-studio-templates.md) 요소가 템플릿의 식별자로 사용됩니다.

 `TemplateID` 요소의 값은 프로젝트 시스템 등록(HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\프로젝트)와\\함께 새 항목 **추가** 대화 상자에 나타나는 템플릿을 필터링하는 데 사용됩니다.

## <a name="see-also"></a>참조
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)

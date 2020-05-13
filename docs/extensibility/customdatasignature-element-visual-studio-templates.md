---
title: 사용자 정의 데이터 서명 요소 (비주얼 스튜디오 템플릿) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <CustomDataSignature> Element (Visual Studio Templates)
- CustomDataSignature Element (Visual Studio Templates)
ms.assetid: 8c3db51d-7014-4484-802a-15aa1353dbdb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec8bae34da0f007bac65f26c4e442c1d03e56d08
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739434"
---
# <a name="customdatasignature-element-visual-studio-templates"></a>사용자 지정 데이터 서명 요소(비주얼 스튜디오 템플릿)
사용자 지정 데이터를 찾으려면 텍스트 서명을 지정합니다.

 \<VS템플릿 \<> 템플릿데이터> \<사용자 정의 데이터 서명>

## <a name="syntax"></a>구문

```
<CustomDataSignature>"string"</CustomDataSignature>
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

 텍스트는 사용자 지정 데이터를 찾는 데 필요한 텍스트 서명이 있는 문자열입니다.

## <a name="remarks"></a>설명
 `CustomDataSignature`는 선택적 요소입니다.

## <a name="see-also"></a>참조
- [비주얼 스튜디오 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)

---
title: PreviewImage 요소 (Visual Studio 템플릿) | Microsoft Docs
description: PreviewImage 요소에 대해 알아보고, 새 프로젝트 또는 새 항목 추가 대화 상자에 표시 되는 미리 보기 이미지의 파일 이름을 지정 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 326588259203224d3f70b505af8437af22930faa
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672348"
---
# <a name="previewimage-element-visual-studio-templates"></a>PreviewImage 요소 (Visual Studio 템플릿)
**새 프로젝트** 또는 **새 항목 추가** 대화 상자에 표시 되는 미리 보기 이미지에 대 한 미리 보기 이미지를 파일 이름으로 지정 합니다.

 \<VSTemplate> \<TemplateData>
 \<PreviewImage>

## <a name="syntax"></a>구문

```
<PreviewImage>"filename"</PreviewImage>
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

 텍스트는 파일 이름을 나타내는 문자열 이어야 합니다.

## <a name="remarks"></a>설명
 `PreviewImage`는 선택적 요소입니다.

## <a name="see-also"></a>참조
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)

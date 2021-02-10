---
title: TargetPlatformName 요소 (Visual Studio 템플릿) | Microsoft Docs
description: TargetPlatformName 요소 및 프로젝트 템플릿이 대상으로 하는 플랫폼을 지정 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 3a6b1f45-b5d6-418e-add1-87ee8f15033d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1f2b8903c99e5bd2f62587b7921be855e4ed6323
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938774"
---
# <a name="targetplatformname-element-visual-studio-templates"></a>TargetPlatformName 요소(Visual Studio 템플릿)
프로젝트 템플릿의 대상 플랫폼을 지정합니다. 이 요소는 프로젝트 템플릿을 사용하여 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 앱을 만들도록 지정하는 데 사용됩니다.

## <a name="syntax"></a>구문

```xml
<VSTemplate>
    <TemplateData>
        <TargetPlatformName> OperatingSystem</TargetPlatformName>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|[RequiredPlatformVersion](../extensibility/requiredplatformversion-element-visual-studio-templates.md)|프로젝트 템플릿의 대상 운영 체제 버전을 지정합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|템플릿을 분류하고 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에서 템플릿이 표시되는 방식을 정의합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

## <a name="remarks"></a>설명
 텍스트는 **Windows** 여야 합니다.

## <a name="example"></a>예제
 이 예제에서는 프로젝트 템플릿이 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 이상을 대상으로 하도록 지정합니다.

```xml
<VSTemplate Type="Project" Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <TargetPlatformName>Windows</TargetPlatformName>
        <RequiredPlatformVersion>8</RequiredPlatformVersion>
    </TemplateData>
    <TemplateContent> </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>참고 항목
- [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)

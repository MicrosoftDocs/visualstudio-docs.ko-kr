---
title: CustomParameters 요소 (Visual Studio 템플릿) | Microsoft Docs
description: CustomParameters 요소에 대해 알아보고 마법사에서 매개 변수를 바꿀 때 템플릿 마법사에 전달할 사용자 지정 매개 변수를 그룹화 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a899790890bd299dcb77558d31499b0a61bcefe4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927134"
---
# <a name="customparameters-element-visual-studio-templates"></a>CustomParameters 요소 (Visual Studio 템플릿)
마법사에서 매개 변수 대체를 만들 때 템플릿 마법사에 전달할 사용자 지정 매개 변수를 그룹화 합니다.

## <a name="syntax"></a>구문

```
<CustomParameters>
    <CustomParameter/>
    <CustomParameter/>
</CustomParameters>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> 템플릿에서 프로젝트 또는 항목을 만들 때 사용할 사용자 지정 매개 변수 이름 및 값을 포함 합니다. `CustomParameter` 요소에는 `CustomParameters` 요소가 0개 또는 그 이상 있을 수 있습니다.|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|템플릿의 내용을 지정 합니다.|

## <a name="remarks"></a>설명

## <a name="example"></a>예제
 다음 예제에서는 템플릿에서 여러 사용자 지정 매개 변수를 사용 하는 방법을 보여 줍니다. 다음 사용자 지정 매개 변수를 사용 하 여 템플릿에서 프로젝트 또는 항목을 만들 때 템플릿 파일의 및의 모든 인스턴스 `$color1$` `$color2$` 는 각각 및로 바뀝니다 `Red` `Blue` .

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>참고 항목
- [CustomParameter 요소 (Visual Studio 템플릿)](../extensibility/customparameter-element-visual-studio-templates.md)
- [템플릿 매개 변수](../ide/template-parameters.md)
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)

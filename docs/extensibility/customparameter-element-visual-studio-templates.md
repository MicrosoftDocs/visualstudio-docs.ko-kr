---
title: CustomParameter 요소 (Visual Studio 템플릿) | Microsoft Docs
description: CustomParameter 요소에 대해 알아보고 템플릿에서 프로젝트 또는 항목을 만들 때 사용할 사용자 지정 매개 변수 이름 및 값을 포함 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61c118bbc85064beb10b99641f0803af7af12d56
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671951"
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter 요소 (Visual Studio 템플릿)
템플릿에서 프로젝트 또는 항목을 만들 때 사용할 사용자 지정 매개 변수 이름 및 값을 포함 합니다.

## <a name="syntax"></a>구문

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|`Name`|필수 사항입니다. 매개 변수의 이름입니다. 매개 변수의 형식은 $*name*$입니다.|
|`Value`|필수 요소. 매개 변수의 대체 값입니다.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|마법사에서 매개 변수 대체를 만들 때 템플릿 마법사에 전달할 사용자 지정 매개 변수를 그룹화 합니다.|

## <a name="remarks"></a>설명
 템플릿에 요소가 포함 된 경우 `CustomParameter` 모든 인스턴스는 `Name` 생성 된 `Value` 프로젝트 또는 항목 파일의 특성으로 대체 됩니다.

## <a name="example"></a>예제
 다음 예제에서는 템플릿에서 여러 사용자 지정 매개 변수를 사용 하는 방법을 보여 줍니다. 다음 사용자 지정 매개 변수를 사용 하 여 템플릿에서 프로젝트 또는 항목을 만들 때 템플릿 파일의 및의 모든 인스턴스 `$color1$` `$color2$` 는 각각 및로 바뀝니다 `Red` `Blue` .

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>참조
- [CustomParameters 요소 (Visual Studio 템플릿)](../extensibility/customparameters-element-visual-studio-templates.md)
- [템플릿 매개 변수](../ide/template-parameters.md)
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)

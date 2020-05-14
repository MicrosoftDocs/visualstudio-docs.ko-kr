---
title: 사용자 정의 매개 변수 요소 (비주얼 스튜디오 템플릿) | 마이크로 소프트 문서
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f524996c226f001c68ddc7ac9aa8cb3b99857fc5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739415"
---
# <a name="customparameters-element-visual-studio-templates"></a>사용자 지정매개 변수 요소(비주얼 스튜디오 템플릿)
마법사가 매개 변수를 대체할 때 템플릿 마법사에 전달할 사용자 지정 매개 변수를 그룹합니다.

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
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> 템플릿에서 프로젝트 또는 항목을 만들 때 사용할 사용자 지정 매개 변수 이름과 값을 포함합니다. `CustomParameter` 요소에는 `CustomParameters` 요소가 0개 또는 그 이상 있을 수 있습니다.|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|템플릿의 내용을 지정합니다.|

## <a name="remarks"></a>설명

## <a name="example"></a>예제
 다음 예제에서는 템플릿에서 여러 사용자 지정 매개 변수를 사용하는 방법을 보여 주며 있습니다. 다음과 같은 사용자 지정 매개 변수가 있는 템플릿에서 프로젝트 `$color1$` 또는 `$color2$` 항목을 만들면 템플릿 `Red` 파일의 모든 인스턴스와 및 `Blue`템플릿 파일의 모든 인스턴스가 각각 및 로 대체됩니다.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>참조
- [사용자 정의 매개 변수 요소 (비주얼 스튜디오 템플릿)](../extensibility/customparameter-element-visual-studio-templates.md)
- [템플릿 매개 변수](../ide/template-parameters.md)
- [비주얼 스튜디오 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)

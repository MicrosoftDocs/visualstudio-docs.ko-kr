---
title: Bitmaps 요소 | Microsoft Docs
description: Bitmaps 요소는 하나 이상의 비트맵 요소를 그룹화합니다. 이 문서에는 Bitmaps 요소의 예가 포함되어 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: 74652e1b-fcfa-421b-aa9f-fbc081d3b476
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a86943e683502bdd1cd19668e9aafcb8fe7e1bc8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903309"
---
# <a name="bitmaps-element"></a>Bitmaps 요소
[Bitmap 요소 요소를](../extensibility/bitmap-element.md) 그룹화합니다.

## <a name="syntax"></a>구문

```
<Bitmaps>
  <Bitmap>... </Bitmap>
  <Bitmap>... </Bitmap>
</Bitmaps>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|조건|선택 사항입니다. [조건부 특성을](../extensibility/vsct-xml-schema-conditional-attributes.md)참조하세요.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[Bitmaps 요소](../extensibility/bitmaps-element.md)|비트맵 요소를 그룹화합니다.|
|[Bitmap 요소](../extensibility/bitmap-element.md)|비트맵을 정의합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Commands 요소](../extensibility/commands-element.md)|VSPackage 도구 모음의 명령 컬렉션을 나타냅니다.|

## <a name="example"></a>예제

```
<Bitmaps>
  <Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
  <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
    usedList="1, 2, 3, 4"/>
</Bitmaps>
```

## <a name="see-also"></a>참조
- [VSPackages에서 사용자 인터페이스 요소를 추가하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)

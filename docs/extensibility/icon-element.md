---
title: Icon 요소 | Microsoft Docs
description: 사용 된 비트맵 및 비트맵 스트립의 슬롯에 대 한 특성이 포함 된 Visual Studio IDE 확장에 사용 되는 아이콘을 나타내는 Icon 요소에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 52ccb8093b61e0458f7c3caefea6f826609aa51d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082142"
---
# <a name="icon-element"></a>Icon 요소
Icon 태그의 guid 특성은 정의 된 비트맵의 guid입니다. `id`특성은 비트맵 스트립에서 슬롯을 선택 합니다. 이 요소는 선택적입니다. 이 요소에 포함 되지 않은 경우 GuidOfficeIcon의 값 **: msotcidNoIcon** 이 포함 됩니다.

## <a name="syntax"></a>구문

```xml
<Icon guid="guidImages" id="bmpPic1" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|Description|
|---------------|-----------------|
|guid|필수 요소. 정의 된 비트맵의 guid입니다.|
|id|필수 요소. 비트맵 스트립에서 슬롯을 선택 합니다.|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|없음|없음|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[Buttons 요소](../extensibility/buttons-element.md)||

## <a name="see-also"></a>참조
- [Visual Studio 명령 테이블 (.vvsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

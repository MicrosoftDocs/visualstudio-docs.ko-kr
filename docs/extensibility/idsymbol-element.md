---
title: IDSymbol 요소 | Microsoft Docs
description: 'IDSymbol 요소는 메뉴, 그룹 또는 명령을 나타내는 GUID: ID 쌍의 ID를 포함 합니다.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f59089ab981bc97100386b3e1907ef903ede3bd0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069844"
---
# <a name="idsymbol-element"></a>IDSymbol 요소
`IDSymbol`요소는 메뉴, 그룹 또는 명령을 나타내는 GUID: id 쌍의 id를 포함 합니다. GUID는 부모 요소에서 가져옵니다 `GuidSymbol` . 요소에는 `IDSymbol` `name` 특성에 포함 된 ID에 대 한 친숙 한 이름을 제공 하는 특성이 있습니다 `value` .

## <a name="syntax"></a>구문

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|Description|
|---------------|-----------------|
|name|필수 요소. ID 기호의 이름입니다.|
|값|필수 요소. ID 기호의 숫자 ID 값입니다.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[GuidSymbol 요소](../extensibility/guidsymbol-element.md)|메뉴, 그룹 또는 명령을 나타내는 GUID: ID 쌍의 GUID를 포함 합니다. `IDSymbol` 요소를 그룹화합니다.|

## <a name="remarks"></a>설명
 `IDSymbol`지정 된 요소의 모든 요소에 `GuidSymbol` 는 고유한가 있어야 합니다 `value` . 그러나 `IDSymbol` 동일한 값을 가진 요소는 부모 항목이 다른 경우 패키지에 있을 수 있습니다.

## <a name="see-also"></a>참조
- [Visual Studio 명령 테이블 (.vvsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

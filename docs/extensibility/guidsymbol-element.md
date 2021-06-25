---
title: GuidSymbol 요소 | Microsoft Docs
description: GuidSymbol 요소는 메뉴, 그룹 또는 명령을 나타내는 GUID:ID 쌍의 GUID를 포함합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7c30c7a48b03b5deed3267e106e926d3cb5114c1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902763"
---
# <a name="guidsymbol-element"></a>GuidSymbol 요소
`GuidSymbol`요소는 메뉴, 그룹 또는 명령을 나타내는 GUID:ID 쌍의 GUID를 포함합니다. ID는 `IDSymbol` 요소의 요소에서 `GuidSymbol` 제공됩니다. `GuidSymbol`요소에는 `name` 특성에 포함된 GUID의 이름을 제공하는 `value` 특성이 있습니다.

## <a name="syntax"></a>구문

```xml
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">
  <IDSymbol>... </IDSymbol>
  <IDSymbol>... </IDSymbol>
</GuidSymbol>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|name|필수 요소. GUID 기호의 이름입니다.|
|value|필수 요소. GUID 기호의 GUID입니다.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[IDSymbol 요소](../extensibility/idsymbol-element.md)|메뉴, 그룹 또는 명령을 나타내는 GUID:ID 쌍의 ID를 포함합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Symbols 요소](../extensibility/symbols-element.md)|`GuidSymbol` *.vsct* 파일의 요소를 그룹화합니다.|

## <a name="remarks"></a>설명
 일반적으로 *.vsct* 파일은 해당 섹션에 패키지 자체에 대한 요소 1개, `GuidSymbol` `Symbols` 명령 집합(패키지에서 사용할 수 있는 메뉴, 그룹 및 명령 컬렉션) 및 단추 및 기타 시각적 구성 요소에 대한 아이콘을 제공하는 비트맵에 대한 요소 3개를 포함합니다. 지정된 요소의 모든 `IDSymbol` `GuidSymbol` 요소에는 고유한 가 있어야 `value` 합니다. 그러나 동일한 값을 가진 요소는 서로 다른 부모가 있는 한 `IDSymbol` 패키지에 존재할 수 있습니다.

## <a name="see-also"></a>참조
- [Visual Studio 명령 테이블(.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

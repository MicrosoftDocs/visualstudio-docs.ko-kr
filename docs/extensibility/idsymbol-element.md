---
title: ID 기호 요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d02a26a6874165738d917a14986d16d142c01915
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710370"
---
# <a name="idsymbol-element"></a>ID 기호 요소
요소에는 `IDSymbol` 메뉴, 그룹 또는 명령을 나타내는 GUID:ID 쌍의 ID가 포함되어 있습니다. GUID는 부모 `GuidSymbol` 요소에서 제공됩니다. 요소에는 `IDSymbol` 특성에 `name` 포함된 ID에 대한 친숙한 이름을 제공하는 `value` 특성이 있습니다.

## <a name="syntax"></a>구문

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|name|필수 사항입니다. ID 기호의 이름입니다.|
|값|필수 사항입니다. ID 기호의 숫자 ID 값입니다.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[Guid Symbol 요소](../extensibility/guidsymbol-element.md)|메뉴, 그룹 또는 명령을 나타내는 GUID:ID 쌍의 GUID를 포함합니다. `IDSymbol` 요소를 그룹화합니다.|

## <a name="remarks"></a>설명
 지정된 `IDSymbol` `GuidSymbol` 요소의 모든 요소에는 `value`고유한 . 그러나 `IDSymbol` 동일한 값을 가진 요소는 서로 다른 부모가 있는 한 패키지에 존재할 수 있습니다.

## <a name="see-also"></a>참조
- [비주얼 스튜디오 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

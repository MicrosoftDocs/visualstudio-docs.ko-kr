---
title: Guid 기호 요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59068a9ac9f952b5370681b3684ce4234354afc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711123"
---
# <a name="guidsymbol-element"></a>Guid Symbol 요소
요소에는 `GuidSymbol` 메뉴, 그룹 또는 명령을 나타내는 GUID:ID 쌍의 GUID가 포함되어 있습니다. ID는 요소의 `IDSymbol` `GuidSymbol` 요소에서 제공됩니다. 요소에는 `GuidSymbol` 속성에 `name` 포함된 GUID에 대해 친숙한 이름을 제공하는 `value` 특성이 있습니다.

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
|name|필수 사항입니다. GUID 기호의 이름입니다.|
|값|필수 사항입니다. GUID 기호의 GUID입니다.|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|[ID 기호 요소](../extensibility/idsymbol-element.md)|메뉴, 그룹 또는 명령을 나타내는 GUID:ID 쌍의 ID를 포함합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[기호 요소](../extensibility/symbols-element.md)|`GuidSymbol` *.vsct* 파일의 요소를 그룹화합니다.|

## <a name="remarks"></a>설명
 일반적으로 *.vsct* 파일에는 `GuidSymbol` 패키지 자체에 `Symbols` 대한 세 가지 요소가 포함되어 있으며, 하나는 명령 집합(패키지에서 사용할 수 있는 메뉴, 그룹 및 명령의 컬렉션)과 단추 및 기타 시각적 구성 요소에 대한 아이콘을 제공하는 비트맵에 대한 요소가 포함되어 있습니다. 지정된 `IDSymbol` `GuidSymbol` 요소의 모든 요소에는 `value`고유한 . 그러나 `IDSymbol` 동일한 값을 가진 요소는 서로 다른 부모가 있는 한 패키지에 존재할 수 있습니다.

## <a name="see-also"></a>참조
- [비주얼 스튜디오 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

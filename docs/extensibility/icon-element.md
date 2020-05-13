---
title: 아이콘 요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf4f8a69e565620007fba4b9970ce96bb1513995
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710516"
---
# <a name="icon-element"></a>아이콘 요소
아이콘 태그의 guid 특성은 정의된 비트맵의 guid입니다. 특성은 `id` 비트맵 스트립의 슬롯을 선택합니다. 이 요소는 선택적입니다. 이 요소에 포함되지 않은 경우 **guidOfficeIcon:msotcidNoIcon의** 값이 암시됩니다.

## <a name="syntax"></a>구문

```xml
<Icon guid="guidImages" id="bmpPic1" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|guid|필수 사항입니다. 정의된 비트맵의 guid입니다.|
|id|필수 사항입니다. 비트맵 스트립에서 슬롯을 선택합니다.|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|없음|없음|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[단추 요소](../extensibility/buttons-element.md)||

## <a name="see-also"></a>참조
- [비주얼 스튜디오 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

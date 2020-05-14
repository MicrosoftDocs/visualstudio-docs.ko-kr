---
title: 버튼텍스트 요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59308feea2002a18662a7c04b95a92a920f934c4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739913"
---
# <a name="buttontext-element"></a>버튼텍스트 요소
이 필드를 사용하면 다양한 메뉴에 나타나는 텍스트를 지정할 수 있습니다. 기본적으로 `ButtonText` 요소는 메뉴 컨트롤러에 나타납니다. 다른 `ButtonText` 텍스트 필드가 비어 있는 경우에도 요소가 기본값이 됩니다. 다른 `ButtonText` 텍스트 필드를 지정한 경우에도 요소를 비워둘 수 없습니다.

## <a name="syntax"></a>구문

```xml
<ButtonText>My Command</ButtonText>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[문자열 요소](../extensibility/strings-element.md)|와 `ButtonText` `CommandName`같은 텍스트 요소를 그룹화합니다.|

## <a name="text-value"></a>텍스트 값
 `ButtonText` 요소의 텍스트 값은 메뉴 항목, 콤보 및 표시되는 텍스트가 있는 기타 사용자 인터페이스(UI) 요소에 대해 표시되는 텍스트를 제공합니다.

## <a name="see-also"></a>참조
- [비주얼 스튜디오 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

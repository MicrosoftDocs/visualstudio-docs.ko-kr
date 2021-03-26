---
title: KeyBinding 요소 | Microsoft Docs
description: KeyBinding 요소는 명령에 대 한 바로 가기 키를 지정 합니다. 명령에는 연결 된 단일 및 이중 키 바인딩이 모두 포함 될 수 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9162d9b21c54577e48f4dced6ddddd7138c9de66
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074095"
---
# <a name="keybinding-element"></a>KeyBinding 요소
KeyBinding 요소는 명령에 대 한 바로 가기 키를 지정 합니다.

 명령에는 연결 된 단일 및 이중 키 바인딩이 모두 포함 될 수 있습니다. 단일 키 바인딩의 예는  + **저장** 명령에 대 한 Ctrl **S** 입니다. 이중 키 바인딩에는 명령을 트리거하는 두 개의 연속 키 조합이 필요 합니다. 이중 키 바인딩의 예는 <strong>ctrl *+</strong> k <strong>,</strong>ctrl <strong>+</strong> k**로 책갈피를 설정 하는 것입니다.

## <a name="syntax"></a>구문

```
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|Description|
|---------------|-----------------|
|guid|필수 요소.|
|id|필수 요소.|
|편집기|필수 요소. 편집기 GUID는이 바로 가기 키가 활성화 될 편집 컨텍스트를 나타냅니다. 전역 바인딩 범위 값은 "guidVSStd97"입니다.|
|key1|필수 요소. 유효한 값은 모든 typable 영숫자를 포함 하 고 0x 및 [VK_constants](/windows/desktop/inputdev/virtual-key-codes)앞에 오는 두 자리 16 진수 값을 포함 합니다.|
|mod1|선택 사항입니다. 공백으로 구분 된 **Ctrl**, **Alt** 및 **Shift** 의 조합입니다.|
|key2|선택 사항입니다. 유효한 값은 모든 typable 영숫자를 포함 하 고 0x 및 [VK_constants](/windows/desktop/inputdev/virtual-key-codes)앞에 오는 두 자리 16 진수 값을 포함 합니다.|
|mod2|선택 사항입니다. 공백으로 구분 된 **Ctrl**, **Alt** 및 **Shift** 의 조합입니다.|
|에뮬레이터|선택 사항입니다.|
|조건|선택 사항입니다. [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)을 참조 하세요.|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|Parent||
|Annotation||

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[KeyBindings 요소](../extensibility/keybindings-element.md)|KeyBinding 요소 및 기타 키 바인딩 그룹을 그룹화 합니다.|

## <a name="example"></a>예제

```
<KeyBindings>
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"
    editor="guidWidgetEditor" key1="VK_F5"/>
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>
</KeyBindings>
```

## <a name="see-also"></a>참조
- [KeyBindings 요소](../extensibility/keybindings-element.md)
- [Visual Studio 명령 테이블 (.vvsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

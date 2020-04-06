---
title: 키바인딩 요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b458e70a9a85c11707c50da2e16e3aa73f51bc12
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703139"
---
# <a name="keybinding-element"></a>키 바인딩 요소
KeyBinding 요소는 명령에 대한 키보드 단축키를 지정합니다.

 명령에는 단일 키 바인딩과 이중 키 바인딩이 모두 연결될 수 있습니다. 단일 키 바인딩의 예는 **저장** 명령에 대한 **Ctrl**+**S입니다.** 이중 키 바인딩에는 명령을 트리거하려면 두 개의 연속키 조합이 필요합니다. 이중 키 바인딩의 예로는 책갈피를 설정하는 <strong>*+</strong>Ctrl<strong>K,</strong>Ctrl<strong>+</strong>K**가 있습니다.

## <a name="syntax"></a>구문

```
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|guid|필수 사항입니다.|
|id|필수 사항입니다.|
|편집기|필수 사항입니다. 편집기 GUID는 이 키보드 단축성이 활성화될 편집 컨텍스트를 나타냅니다. 전역 바인딩 범위 값은 "guidVSStd97"입니다.|
|key1|필수 사항입니다. 유효한 값에는 모든 입력 가능한 영숫자와 0x 및 [VK_constants](/windows/desktop/inputdev/virtual-key-codes)앞에 오는 두 자리 헥사데피만 값이 포함됩니다.|
|모드 1|(선택 사항) **Ctrl,** **Alt**및 **Shift의** 모든 조합은 공간으로 구분됩니다.|
|key2|(선택 사항) 유효한 값에는 모든 입력 가능한 영숫자와 0x 및 [VK_constants](/windows/desktop/inputdev/virtual-key-codes)앞에 오는 두 자리 헥사데피만 값이 포함됩니다.|
|모드2|(선택 사항) **Ctrl,** **Alt**및 **Shift의** 모든 조합은 공간으로 구분됩니다.|
|에뮬레이터|(선택 사항)|
|조건|(선택 사항) [조건부 특성을](../extensibility/vsct-xml-schema-conditional-attributes.md)참조하십시오.|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|Parent||
|주석||

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[키 바인딩 요소](../extensibility/keybindings-element.md)|키 바인딩 요소 및 기타 키 바인딩 그룹화 그룹입니다.|

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
- [키 바인딩 요소](../extensibility/keybindings-element.md)
- [비주얼 스튜디오 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

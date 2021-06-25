---
title: KeyBinding 요소 | Microsoft Docs
description: KeyBinding 요소는 명령에 대한 바로 가기 키를 지정합니다. 명령에는 단일 및 이중 키 바인딩이 모두 연결될 수 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6afd0a9658f088b66f2c18c632ffcd7b9a09f555
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898863"
---
# <a name="keybinding-element"></a>KeyBinding 요소
KeyBinding 요소는 명령에 대한 바로 가기 키를 지정합니다.

 명령에는 단일 및 이중 키 바인딩이 모두 연결될 수 있습니다. 단일 키 바인딩의 예는 저장 명령에 대한 **Ctrl** + **S입니다.**  이중 키 바인딩은 명령을 트리거하기 위해 두 개의 연속 키 조합이 필요합니다. 이중 키 바인딩의 예로는 책갈피를 설정하는 <strong> *+</strong> Ctrl K <strong>,</strong>Ctrl <strong>+</strong> K**가 있습니다.

## <a name="syntax"></a>구문

```
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|guid|필수 요소.|
|id|필수 요소.|
|편집기|필수 요소. 편집기 GUID는 이 바로 가기 키가 활성화될 편집 컨텍스트를 나타냅니다. 전역 바인딩 범위 값은 "guidVSStd97"입니다.|
|key1|필수 요소. 유효한 값에는 입력 가능한 모든 영숫자와 0x 및 [VK_constants](/windows/desktop/inputdev/virtual-key-codes)앞에 오는 두 자리 16진수 값이 포함됩니다.|
|mod1|선택 사항입니다. 공백으로 구분된 **Ctrl,** **Alt** 및 **Shift의** 모든 조합입니다.|
|key2|선택 사항입니다. 유효한 값에는 입력 가능한 모든 영숫자와 0x 및 [VK_constants](/windows/desktop/inputdev/virtual-key-codes)앞에 오는 두 자리 16진수 값이 포함됩니다.|
|mod2|선택 사항입니다. 공백으로 구분된 **Ctrl,** **Alt** 및 **Shift의** 모든 조합입니다.|
|에뮬레이터|선택 사항입니다.|
|조건|선택 사항입니다. [조건부 특성을](../extensibility/vsct-xml-schema-conditional-attributes.md)참조하세요.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|Parent||
|Annotation||

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[KeyBindings 요소](../extensibility/keybindings-element.md)|KeyBinding 요소 및 기타 KeyBindings 그룹화 그룹을 그룹화합니다.|

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
- [Visual Studio 명령 테이블(.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

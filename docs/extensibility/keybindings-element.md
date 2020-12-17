---
title: KeyBindings 요소 | Microsoft Docs
description: KeyBindings 요소는 KeyBinding 요소 및 기타 키 바인딩 그룹을 그룹화 합니다. 이 문서에는 예제가 포함 되어 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- KeyBindings
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBindings element (VSCT XML schema)
ms.assetid: 26a15d5c-ddea-4977-af7f-d795ff09c7ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 928637d8103a69eafd3bda4446a55bb7523f83a8
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97616093"
---
# <a name="keybindings-element"></a>KeyBindings 요소
KeyBindings 요소는 KeyBinding 요소 및 기타 키 바인딩 그룹을 그룹화 합니다.

## <a name="syntax"></a>구문

```xml
<KeyBindings>
  <KeyBinding>... </KeyBinding>
  <KeyBinding>... </KeyBinding>
</KeyBindings>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|조건|선택 사항입니다. [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)을 참조 하세요.|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|[KeyBinding 요소](../extensibility/keybinding-element.md)|명령에 대 한 바로 가기 키를 지정 합니다.|
|[KeyBindings](../extensibility/keybindings-element.md)|KeyBinding 요소 및 기타 키 바인딩 그룹을 그룹화 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[CommandTable 요소](../extensibility/commandtable-element.md)|명령을 나타내는 모든 요소를 정의 합니다.|

## <a name="example"></a>예제

```xml
<KeyBindings>
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"
    editor="guidWidgetEditor" key1="VK_F5"/>
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>
</KeyBindings>
```

## <a name="see-also"></a>참고 항목
- [KeyBinding 요소](../extensibility/keybinding-element.md)
- [Visual Studio 명령 테이블 (.vvsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

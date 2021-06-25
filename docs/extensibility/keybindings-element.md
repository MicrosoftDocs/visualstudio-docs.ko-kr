---
title: KeyBindings 요소 | Microsoft Docs
description: KeyBindings 요소는 KeyBinding 요소 및 기타 KeyBindings 그룹화 그룹을 그룹화합니다. 이 문서에는 예제가 포함되어 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- KeyBindings
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBindings element (VSCT XML schema)
ms.assetid: 26a15d5c-ddea-4977-af7f-d795ff09c7ad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 128b28ff77515ac4b567ecdb8f536851da4d33ce
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903374"
---
# <a name="keybindings-element"></a>KeyBindings 요소
KeyBindings 요소는 KeyBinding 요소 및 기타 KeyBindings 그룹화 그룹을 그룹화합니다.

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
|조건|선택 사항입니다. [조건부 특성을](../extensibility/vsct-xml-schema-conditional-attributes.md)참조하세요.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[KeyBinding 요소](../extensibility/keybinding-element.md)|명령의 바로 가기 키를 지정합니다.|
|[KeyBindings](../extensibility/keybindings-element.md)|KeyBinding 요소 및 기타 KeyBindings 그룹화 그룹을 그룹화합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CommandTable 요소](../extensibility/commandtable-element.md)|명령을 나타내는 모든 요소를 정의합니다.|

## <a name="example"></a>예제

```xml
<KeyBindings>
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"
    editor="guidWidgetEditor" key1="VK_F5"/>
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>
</KeyBindings>
```

## <a name="see-also"></a>참조
- [KeyBinding 요소](../extensibility/keybinding-element.md)
- [Visual Studio 명령 테이블(.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

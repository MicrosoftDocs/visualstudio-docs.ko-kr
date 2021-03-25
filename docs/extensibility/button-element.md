---
title: Button 요소 | Microsoft Docs
description: Button 요소는 사용자가 상호 작용할 수 있는 요소를 정의 합니다. Button, MenuButton 및 SplitDropDown 단추를 사용할 수 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec0640313195d6a15599d1a765081557c0c1a75a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068146"
---
# <a name="button-element"></a>Button 요소
사용자가 조작할 수 있는 요소를 정의 합니다. 단추, MenuButton 및 SplitDropDown 단추가 다를 수 있습니다.

## <a name="syntax"></a>구문

```
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">
  <Parent>... </Parent>
  <Icon>... </Icon>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Button>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|Description|
|---------------|-----------------|
|guid|필수 요소. GUID/ID 명령 식별자의 GUID입니다.|
|id|필수 요소. GUID/ID 명령 식별자의 ID입니다.|
|priority|선택 사항입니다. 우선 순위를 지정 하는 숫자 값입니다.|
|형식|선택 사항입니다. 단추의 종류를 지정 하는 열거형 값입니다.<br /><br /> 지정 하지 않으면 단추를 사용 합니다.<br /><br /> 단추<br /> 도구 모음 (일반적으로 아이콘 단추), 메뉴 및 상황에 맞는 메뉴에 표시 되는 표준 명령입니다.<br /><br /> MenuButton<br /> 명령을 실행 하지 않고 다른 메뉴를 생성 하는 메뉴 항목입니다.<br /><br /> SplitDropDown<br /> Microsoft Word의 표준 도구 모음에 있는 실행 취소 및 다시 실행 단추와 같은 컨트롤입니다.|
|조건|선택 사항입니다. [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)을 참조 하세요.|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|[부모 요소](../extensibility/parent-element.md)|선택 사항입니다. 단추의 부모 요소입니다.|
|[Icon 요소](../extensibility/icon-element.md)|선택 사항입니다. 단추와 연결 된 아이콘입니다.|
|[명령 플래그 요소](../extensibility/command-flag-element.md)|필수 요소. 단추에 대 한 유효한 CommandFlag 값은 다음과 같습니다.<br /><br /> -AllowParams<br /><br /> - CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> - NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> - RouteToDocs<br /><br /> - TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -TextChanges<br /><br /> -Text) 단추<br /><br /> -TextContextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|
|[Strings 요소](../extensibility/strings-element.md)|필수 요소. 자식 [Buttontext 요소](../extensibility/buttontext-element.md) 를 정의 해야 합니다.|
|Annotation|선택적 설명입니다.|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[Buttons 요소](../extensibility/buttons-element.md)|단추 요소를 그룹화 합니다.|

## <a name="example"></a>예제
 다음 예제에서는 *. vsct* 파일의 단추를 정의 합니다.

 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```

## <a name="see-also"></a>참조
- [Visual Studio 명령 테이블 (.vvsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

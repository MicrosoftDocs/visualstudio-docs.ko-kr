---
title: CommandPlacement 요소 | Microsoft Docs
description: CommandPlacement 요소를 사용 하면 단추, 그룹 및 메뉴를 두 개 이상의 그룹이 나 메뉴에 포함할 수 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 69be89fb2773be9de632b8059cf217303daaede7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901996"
---
# <a name="commandplacement-element"></a>CommandPlacement 요소
CommandPlacement 요소를 사용 하면 단추, 그룹 및 메뉴를 두 개 이상의 그룹이 나 메뉴에 포함할 수 있습니다. CommandPlacement 요소를 사용 하면 사용자 인터페이스의 모양을 수정 하기 위해 이러한 항목을 완전히 다시 정의할 필요가 없습니다.

 자세한 내용은 [다시 사용할 수 있는 단추 그룹 만들기](../extensibility/creating-reusable-groups-of-buttons.md)를 참조 하세요.

## <a name="syntax"></a>구문

```
<CommandPlacement guid="guidMyCommandSet" id="MyCommand" priority="0x001" >
  <Parent>... </Parent>
</CommandPlacement>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|guid|필수 요소. [기호 요소](../extensibility/symbols-element.md)에 정의 된 대로 명령 집합의 guid입니다.|
|id|필수 요소. 에 정의 된 대로 배치할 메뉴, 그룹 또는 명령의 id입니다 `Symbols Element` .|
|priority|필수 요소. 부모 요소에서 항목의 시각적 위치를 결정 합니다.|
|조건|선택 사항입니다. [조건부 Aattributes](../extensibility/vsct-xml-schema-conditional-attributes.md)를 참조 하세요.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|Parent|필수 요소. 배치할 항목을 호스팅하는 메뉴 또는 그룹입니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CommandPlacements 요소](../extensibility/commandplacements-element.md)|Commandplacements 및 Commandplacements 요소의 그룹을 지정 합니다.|

## <a name="example"></a>예제

```
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>참조
- [CommandPlacements 요소](../extensibility/commandplacements-element.md)
- [Visual Studio 명령 테이블 (.vvsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

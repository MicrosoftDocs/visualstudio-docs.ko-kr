---
title: CommandPlacements 요소 | Microsoft Docs
description: CommandPlacements 요소는 CommandPlacement 요소 및 기타 CommandPlacements 그룹화 그룹을 그룹화합니다. CommandPlacements 요소는 선택 사항입니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 21e0feb3913b148b4320e69461bc5035655a392d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901892"
---
# <a name="commandplacements-element"></a>CommandPlacements 요소
CommandPlacements 요소는 CommandPlacement 요소 및 기타 CommandPlacements 그룹화 그룹을 그룹화합니다.

 CommandPlacements 요소는 선택 사항입니다. 명령, 그룹 또는 메뉴가 보조 위치에 포함되어야 하는 경우 *.vsct* 파일에 이 섹션을 포함할 필요가 없습니다.

## <a name="syntax"></a>구문

```xml
<CommandPlacements>
  <CommandPlacement>... </CommandPlacement>
  <CommandPlacement>... </CommandPlacement>
</CommandPlacements>
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
|CommandPlacements|CommandPlacement 요소 및 기타 CommandPlacements 그룹화 그룹을 그룹화합니다.|
|[CommandPlacement 요소](../extensibility/commandplacement-element.md)|단추, 그룹 및 메뉴를 두 개 이상의 그룹 또는 메뉴에 포함할 수 있습니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CommandTable 요소](../extensibility/commandtable-element.md)|명령을 나타내는 모든 요소를 정의합니다.|

## <a name="example"></a>예제

```xml
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>참조
- [CommandPlacement 요소](../extensibility/commandplacement-element.md)
- [Visual Studio 명령 테이블(.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

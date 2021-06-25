---
title: Groups 요소 | Microsoft Docs
description: Groups 요소는 VSPackage의 명령 그룹을 정의 하는 항목을 포함 합니다. 이 문서에는 예제가 포함되어 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Groups
- Groups element (VSCT XML schema)
ms.assetid: 740ca4ec-79fa-4b98-8f9a-2a137f9f7f98
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4f20e19e19539e71a4dbed74a0dd5bb9af62a15f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902828"
---
# <a name="groups-element"></a>Groups 요소
VSPackage의 명령 그룹을 정의 하는 항목을 포함 합니다.

## <a name="syntax"></a>구문

```xml
<Groups>
  <Group>... </Group>
  <Group>... </Group>
</Groups>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|조건|선택 사항입니다. [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)을 참조 하세요.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[Group 요소](../extensibility/group-element.md)|단일 명령 그룹을 나타냅니다.|
|[Groups 요소](../extensibility/groups-element.md)|VSPackage의 명령 그룹을 정의 하는 항목을 포함 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Commands 요소](../extensibility/commands-element.md)|VSPackage 도구 모음에 있는 명령 컬렉션을 나타냅니다.|

## <a name="example"></a>예제

```xml
<Groups>
  <Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
    <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/>
  </Group>
</Groups>
```

## <a name="see-also"></a>참조
- [Vspackage 사용자 인터페이스 요소를 추가 하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)

---
title: 그룹 요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Groups
- Groups element (VSCT XML schema)
ms.assetid: 740ca4ec-79fa-4b98-8f9a-2a137f9f7f98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6383c3c7a28f9aa7778fddcbfe36b237d21323f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711182"
---
# <a name="groups-element"></a>Groups 요소
VSPackage의 명령 그룹을 정의하는 항목을 포함합니다.

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
|조건|(선택 사항) [조건부 특성을](../extensibility/vsct-xml-schema-conditional-attributes.md)참조하십시오.|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|[Group 요소](../extensibility/group-element.md)|단일 명령 그룹을 나타냅니다.|
|[요소 그룹](../extensibility/groups-element.md)|VSPackage의 명령 그룹을 정의하는 항목을 포함합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[명령 요소](../extensibility/commands-element.md)|VSPackage 도구 모음에서 명령 컬렉션을 나타냅니다.|

## <a name="example"></a>예제

```xml
<Groups>
  <Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
    <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/>
  </Group>
</Groups>
```

## <a name="see-also"></a>참조
- [VSPackage사용자 인터페이스 요소를 추가하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)

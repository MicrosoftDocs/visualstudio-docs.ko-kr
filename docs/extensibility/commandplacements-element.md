---
title: 명령 위치 요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a72b087652a654b563fd4e00bacc52290a29fe1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739704"
---
# <a name="commandplacements-element"></a>명령 위치 요소
명령 위치 요소 그룹 명령 위치 요소 및 기타 명령 배치 그룹화합니다.

 명령 위치 요소는 선택 사항입니다. 명령, 그룹 또는 메뉴를 보조 위치에 포함해야 하는 경우 *.vsct* 파일에 이 섹션을 포함할 필요가 없습니다.

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
|조건|(선택 사항) [조건부 특성을](../extensibility/vsct-xml-schema-conditional-attributes.md)참조하십시오.|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|명령 위치|그룹 명령 위치 요소 및 기타 명령 배치 그룹화.|
|[명령 위치 요소](../extensibility/commandplacement-element.md)|단추, 그룹 및 메뉴를 두 개 이상의 그룹 또는 메뉴에 포함할 수 있습니다.|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[명령 테이블 요소](../extensibility/commandtable-element.md)|명령을 나타내는 모든 요소를 정의합니다.|

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
- [명령 위치 요소](../extensibility/commandplacement-element.md)
- [비주얼 스튜디오 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

---
title: 명령 위치 요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcf9f23b5e860b895baa4c2a7a783f2ee15fcc77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739733"
---
# <a name="commandplacement-element"></a>명령 위치 요소
CommandPlacement 요소를 사용하면 단추, 그룹 및 메뉴를 두 개 이상의 그룹 또는 메뉴에 포함할 수 있습니다. CommandPlacement 요소를 사용 하 여 사용자 인터페이스의 모양을 수정 하기 위해 이러한 항목을 완전히 재정의 할 필요가 없습니다.

 자세한 내용은 [재사용 가능한 단추 그룹 만들기를](../extensibility/creating-reusable-groups-of-buttons.md)참조하십시오.

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
|guid|필수 사항입니다. [기호 요소에](../extensibility/symbols-element.md)정의된 명령 집합의 guid입니다.|
|id|필수 사항입니다. 에 정의된 대로 배치할 메뉴, 그룹 또는 명령의 `Symbols Element`ID입니다.|
|priority|필수 사항입니다. 상위 요소에서 항목의 시각적 위치를 결정합니다.|
|조건|(선택 사항) [조건부 속성](../extensibility/vsct-xml-schema-conditional-attributes.md)을 참조하십시오.|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|Parent|필수 사항입니다. 배치할 항목을 호스트하는 메뉴 또는 그룹입니다.|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[명령 위치 요소](../extensibility/commandplacements-element.md)|명령 위치 및 명령 배치 요소 의 그룹을 지정합니다.|

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
- [명령 위치 요소](../extensibility/commandplacements-element.md)
- [비주얼 스튜디오 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

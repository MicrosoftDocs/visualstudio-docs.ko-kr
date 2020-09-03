---
title: 부모 요소 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c018505ba06762bf8426f266b24ee1835313c29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702226"
---
# <a name="parent-element"></a>부모 요소
단추나 콤보 상자의 부모는 그룹 일 수만 있습니다. 메뉴 또는 그룹의 부모는 다른 메뉴 또는 그룹 일 수 있습니다. [Commandplacement 요소](../extensibility/commandplacement-element.md)에서이 요소는 필수입니다. 다른 모든 경우에는 선택 사항입니다. 이 요소를 생략 하면의 부모가 암시 됩니다 `Group_Undefined:0` .

## <a name="syntax"></a>구문

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|guid|필수 요소. GUID/ID 명령 식별자의 GUID입니다.|
|id|필수 요소. GUID/ID 명령 식별자의 ID입니다.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CommandTable 요소](../extensibility/commandtable-element.md)|VSPackage가 IDE (통합 개발 환경)에 제공 하는 명령을 나타내는 모든 요소를 정의 합니다. 예를 들어 메뉴 항목, 메뉴, 도구 모음 및 콤보 상자가 있습니다.|
|[Buttons 요소](../extensibility/buttons-element.md)|[단추 요소](../extensibility/button-element.md) 요소를 그룹화 합니다.|
|[Menus 요소](../extensibility/menus-element.md)|VSPackage가 구현 하는 모든 메뉴를 정의 합니다.|
|[Groups 요소](../extensibility/groups-element.md)|VSPackage의 명령 그룹을 정의 하는 항목을 포함 합니다.|

## <a name="see-also"></a>추가 정보
- [Visual Studio 명령 테이블 (.vvsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

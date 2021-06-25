---
title: 부모 요소 | Microsoft Docs
description: Parent 요소는 요소가 단추, 콤보 상자, 메뉴 또는 그룹의 부모임을 지정합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3dbf7202ac7fb94762ea132a2620625fae97ddfb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901554"
---
# <a name="parent-element"></a>부모 요소
단추 또는 콤보 상자의 부모는 그룹일 수 있습니다. 메뉴 또는 그룹의 부모는 다른 메뉴 또는 그룹일 수 있습니다. [CommandPlacement 요소](../extensibility/commandplacement-element.md)에서는 이 요소가 필요합니다. 다른 모든 인스턴스에서는 선택 사항입니다. 이 요소를 생략하면 의 부모가 `Group_Undefined:0` 암시됩니다.

## <a name="syntax"></a>구문

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|guid|필수 요소. GUID/ID 명령 식별자의 GUID입니다.|
|id|필수 요소. GUID/ID 명령 식별자의 ID입니다.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CommandTable 요소](../extensibility/commandtable-element.md)|VSPackage가 IDE(통합 개발 환경)에 제공하는 명령을 나타내는 모든 요소를 정의합니다. 예를 들어 메뉴 항목, 메뉴, 도구 모음 및 콤보 상자가 있습니다.|
|[Buttons 요소](../extensibility/buttons-element.md)|[Button 요소 요소를](../extensibility/button-element.md) 그룹화합니다.|
|[Menus 요소](../extensibility/menus-element.md)|VSPackage가 구현하는 모든 메뉴를 정의합니다.|
|[Groups 요소](../extensibility/groups-element.md)|VSPackage의 명령 그룹을 정의하는 항목을 포함합니다.|

## <a name="see-also"></a>참조
- [Visual Studio 명령 테이블(.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

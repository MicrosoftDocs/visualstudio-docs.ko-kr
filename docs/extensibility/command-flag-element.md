---
title: Command Flag 요소 | Microsoft Docs
description: Command 플래그 요소는 부모 요소를 수정합니다. 부모 요소 및 자식 요소를 검토합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6356fd02c8045aee9dc48ebc9d30a346159080bb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902035"
---
# <a name="command-flag-eelement"></a>명령 플래그 Eelement
부모 요소를 수정합니다.

## <a name="syntax"></a>구문

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 유효한 요소 값에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소

|값|설명|
|-----------|-----------------|
|AllowParams|사용자가 명령의 정식 이름을 입력할 때 **명령** 창에 명령 매개 변수를 입력할 수 있음을 나타냅니다.<br /><br /> 다음의 경우 유효합니다. `Button`|
|AlwaysCreate|메뉴는 그룹이나 단추가 없는 경우에도 만들어집니다.<br /><br /> 다음의 경우 유효합니다. `Menu`|
|CaseSensitive|사용자 항목은 대/소문자를 구분합니다.<br /><br /> 다음의 경우 유효합니다. `Combo`|
|CommandWellOnly|명령이 최상위 메뉴에 표시되지 않고 추가 셸 사용자 지정에 사용할 수 있도록 하려는 경우(예: 바로 가기 키에 바인딩) 이 플래그를 적용합니다. VSPackage를 설치한 후 **옵션** 대화 상자를 열고 **키보드 환경** 범주에서 명령 배치를 편집하여 이러한 명령을 사용자 지정할 수 있습니다. 이 플래그는 바로 가기 메뉴, 도구 모음, 메뉴 컨트롤러 또는 하위 메뉴의 배치에 영향을 주지 않습니다.<br /><br /> 유효 기간: `Button` , `Combo`|
|DefaultDisabled|기본적으로 명령을 구현하는 VSPackage가 로드되지 않았거나 메서드가 호출되지 않은 경우 명령을 `QueryStatus` 사용할 수 없습니다.<br /><br /> 유효 기간: `Button` , `Combo`|
|DefaultDocked|기본적으로 도킹됩니다. 이 설정은 항상 도킹되므로 도구 모음에 더 이상 적용되지 않습니다.|
|DefaultInvisible|기본적으로 명령을 구현하는 VSPackage가 로드되지 않았거나 메서드가 호출되지 않은 경우 명령은 표시되지 `QueryStatus` 않습니다.<br /><br /> 이를 플래그와 결합하는 것이 `DynamicVisibility` 좋습니다.<br /><br /> 유효 기간: `Button` , `Combo` , `Menu`|
|DontCache|개발 환경에서는 이 명령에 대한 메서드 결과를 캐시하지 `QueryStatus` 않습니다.<br /><br /> 메뉴의 경우 메뉴 컨트롤러에 해당 메뉴 항목의 텍스트를 캐시하지 않도록 지시합니다. 동적 텍스트가 있는 항목 또는 동적 항목이 메뉴에 포함된 경우 이 플래그를 사용합니다.<br /><br /> 유효 기간: `Button` , `Menu`|
|DynamicItemStart|동적 목록의 시작을 나타냅니다. 이렇게 하면 환경에서는 `QueryStatus` OLECMDERR_E_UNSUPPORTED 플래그가 반환될 때까지 목록 항목에서 메서드를 연속적으로 호출하여 목록을 작성할 수 있습니다. 이는 가장 최근에 사용한(MRU) 목록 및 창 목록과 같은 항목에 적합합니다.<br /><br /> 다음의 경우 유효합니다. `Button`|
|DynamicVisibility|명령의 표시 유형은 메서드 또는 섹션에 포함된 컨텍스트 GUID를 통해 변경할 수 `QueryStatus` `VisibilityConstraints` 있습니다.<br /><br /> 메뉴 및 도구 창 도구 모음에 표시되지만 주 창에 표시되는 최상위 도구 모음에는 표시되지 않는 명령에 적용됩니다. 메서드에서 OLECMDF_INVISIBLE 플래그가 반환될 때 최상위 도구 모음 항목을 사용하지 않도록 설정하지만 숨길 수는 `QueryStatus` 없습니다. 도구 창 도구 모음에 표시되는 도구 모음 명령을 숨길 수 있습니다.<br /><br /> 또한 메뉴에서 이 플래그는 모든 멤버가 숨겨질 때 자동으로 숨겨야 함을 나타냅니다. 최상위 메뉴에는 이미 이 동작이 있으므로 이 플래그는 일반적으로 하위 메뉴에 할당됩니다.<br /><br /> 이 플래그는 플래그와 결합되어야 `DefaultInvisible` 합니다.<br /><br /> 유효 기간: `Button` , `Combo` , `Menu`|
|FilterKeys|[콤보 요소](../extensibility/combo-element.md)아래의 필터링 키 항목을 참조하세요.<br /><br /> 다음의 경우 유효합니다. `Combo`|
|FixMenuController|이 명령이 메뉴 컨트롤러에 배치되는 경우 명령은 항상 기본값입니다. 즉, 메뉴 컨트롤러 단추 자체가 선택될 때마다 명령이 선택됩니다. 메뉴 컨트롤러에 플래그가 설정된 경우 `TextIsAnchorCommand` 메뉴 컨트롤러는 플래그가 있는 명령에서 해당 텍스트도 `FixMenuController` 받습니다.<br /><br /> 메뉴 컨트롤러에서 하나의 명령에만 `FixMenuController` 플래그가 있어야 합니다. 명령이 두 개 이상 표시되어 있으면 메뉴의 마지막 명령이 기본 명령이 됩니다.<br /><br /> 다음의 경우 유효합니다. `Button`|
|IconAndText|메뉴 및 도구 모음에 아이콘과 텍스트를 표시합니다.<br /><br /> 유효 기간: `Button` , `Combo` , `Menu`|
|NoAutoComplete|자동 완성 기능을 사용할 수 없습니다.<br /><br /> 다음의 경우 유효합니다. `Combo`|
|NoButtonCustomize|사용자가 이 단추를 사용자 지정하도록 허용하지 않습니다.<br /><br /> 유효 기간: `Button` , `Combo`|
|NoKeyCustomize|키보드 사용자 지정을 사용하도록 설정하지 마십시오.<br /><br /> 유효 기간: `Button` , `Combo`|
|NoShowOnMenuController|이 명령이 메뉴 컨트롤러에 있는 경우 명령은 드롭다운 목록에 나타나지 않습니다.<br /><br /> 다음의 경우 유효합니다. `Button`|
|NotInTBList|사용 가능한 도구 모음 목록에 표시되지 않습니다. 도구 모음 메뉴 유형에만 유효합니다.<br /><br /> 다음의 경우 유효합니다. `Menu`|
|NoToolbarClose|사용자가 도구 모음을 닫을 수 없습니다. 도구 모음 메뉴 유형에만 유효합니다.<br /><br /> 다음의 경우 유효합니다. `Menu`|
|Pict|도구 모음에는 아이콘만 표시하고 메뉴에는 텍스트만 표시합니다. 아이콘을 지정하지 않으면 도구 모음에 클릭 가능한 빈 공간이 표시됩니다.<br /><br /> 다음의 경우 유효합니다. `Button`|
|PostExec|명령을 비차단으로 만듭니다. 개발 환경은 모든 전처리 쿼리가 완료될 때까지 실행을 연기합니다.<br /><br /> 다음의 경우 유효합니다. `Button`|
|RouteToDocs|명령은 활성 문서로 라우팅됩니다.<br /><br /> 다음의 경우 유효합니다. `Button`|
|StretchHorizontally|이 플래그를 설정하면 너비가 콤보 상자의 최소 너비가 되고, 도구 모음에 공간이 있는 경우 콤보 상자가 확장되어 사용 가능한 공간을 채웁니다. 이 문제는 도구 모음이 가로로 도킹되고 도구 모음의 콤보 상자 하나만 플래그를 사용할 수 있는 경우에만 발생합니다(플래그는 첫 번째 콤보 상자를 제외한 모든 상자에서 무시됨).<br /><br /> 다음의 경우 유효합니다. `Combo`|
|TextChanges|명령 또는 메뉴 텍스트는 런타임에 일반적으로 메서드를 통해 변경할 수 `QueryStatus` 있습니다.<br /><br /> 유효 기간: `Button` , `Menu`|
|TextChangesButton|다음의 경우 유효합니다. `Button`|
|TextIsAnchorCommand|메뉴 컨트롤러의 경우 메뉴의 텍스트는 기본(앵커) 명령에서 가져온 것입니다. 앵커 명령은 선택되거나 래치된 마지막 명령입니다. 이 플래그가 설정되지 않은 경우 메뉴 컨트롤러는 자체 `MenuText` 필드를 사용합니다. 그러나 메뉴 컨트롤러를 클릭하면 해당 컨트롤러에서 마지막으로 선택한 명령이 계속 활성화됩니다.<br /><br /> 이 플래그를 플래그와 결합하는 것이 `TextChanges` 좋습니다.<br /><br /> 이 플래그는 MenuController 또는 MenuControllerLatched 형식의 메뉴에만 적용됩니다.<br /><br /> 다음의 경우 유효합니다. `Menu`|
|TextMenuCtrlUseMenu|메뉴 `MenuText` 컨트롤러에서 필드를 사용합니다. 기본 필드는 `ButtonText` 입니다.<br /><br /> 다음의 경우 유효합니다. `Button`|
|TextMenuUseButton|`ButtonText`메뉴에 필드를 사용합니다. 기본 필드는 `MenuText` 지정된 경우 입니다.<br /><br /> 다음의 경우 유효합니다. `Button`|
|TextOnly|도구 모음 또는 메뉴에 텍스트만 표시하지만 아이콘이 지정된 경우에도 아이콘은 표시하지 않습니다.<br /><br /> 다음의 경우 유효합니다. `Button`|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Buttons 요소](../extensibility/buttons-element.md)|Button 요소 [요소에](../extensibility/button-element.md) 대한 그룹을 제공합니다.|
|[Menus 요소](../extensibility/menus-element.md)|VSPackage가 구현하는 모든 메뉴를 정의합니다.|

## <a name="see-also"></a>참조
- [Visual Studio 명령 테이블(. Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

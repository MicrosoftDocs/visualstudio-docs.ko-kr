---
title: 명령 플래그 요소 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84138a69dbb42fc349c12276fd7cca4b593e4d47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81649366"
---
# <a name="command-flag-eelement"></a>Command 플래그 Eelement
부모 요소를 수정 합니다.

## <a name="syntax"></a>구문

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 유효한 요소 값에 대해 설명 합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소

|값|설명|
|-----------|-----------------|
|AllowParams|사용자가 명령의 정식 이름을 입력할 때 **명령 창에** 명령 매개 변수를 입력할 수 있음을 나타냅니다.<br /><br /> 유효 기간: `Button`|
|AlwaysCreate|메뉴는 그룹이 나 단추가 없는 경우에도 만들어집니다.<br /><br /> 유효 기간: `Menu`|
|CaseSensitive|사용자 항목은 대/소문자를 구분 합니다.<br /><br /> 유효 기간: `Combo`|
|CommandWellOnly|명령이 최상위 메뉴에 표시 되지 않고 추가 셸 사용자 지정 (예: 바로 가기 키에 바인딩) 할 수 있도록 하려면이 플래그를 적용 합니다. VSPackage가 설치 된 후 **옵션** 대화 상자를 열고 **키보드 환경** 범주 아래의 명령 배치를 편집 하 여 이러한 명령을 사용자 지정할 수 있습니다. 이 플래그는 바로 가기 메뉴, 도구 모음, 메뉴 컨트롤러 또는 하위 메뉴의 배치에 영향을 주지 않습니다.<br /><br /> 유효 기간: `Button` , `Combo`|
|DefaultDisabled|이를 구현 하는 VSPackage이 로드 되지 않았거나 메서드가 호출 되지 않은 경우 기본적으로 명령이 사용 하지 않도록 설정 됩니다 `QueryStatus` .<br /><br /> 유효 기간: `Button` , `Combo`|
|DefaultDocked 됨|기본적으로 도킹 됩니다. 이 설정은 항상 도킹 되어 있으므로 도구 모음에 더 이상 적용 되지 않습니다.|
|DefaultInvisible|기본적으로이 명령은 구현 하는 VSPackage 로드 되지 않았거나 메서드가 호출 되지 않은 경우에는 표시 되지 않습니다 `QueryStatus` .<br /><br /> 플래그와 결합 하는 것이 좋습니다 `DynamicVisibility` .<br /><br /> 유효 기간: `Button` , `Combo` , `Menu`|
|DontCache|개발 환경에서는 `QueryStatus` 이 명령에 대 한 메서드 결과를 캐시 하지 않습니다.<br /><br /> 메뉴의 경우 메뉴 컨트롤러에서 메뉴 항목의 텍스트를 캐시 하지 않도록 지시 합니다. 동적 텍스트가 있는 항목이 나 동적 항목이 메뉴에 포함 되어 있는 경우이 플래그를 사용 합니다.<br /><br /> 유효 기간: `Button` , `Menu`|
|DynamicItemStart|동적 목록의 시작을 나타냅니다. 이렇게 하면 `QueryStatus` OLECMDERR_E_UNSUPPORTED 플래그가 반환 될 때까지 목록 항목에서 메서드를 차례로 호출 하 여 환경을 만들 수 있습니다. 가장 최근에 사용한 (MRU) 목록 및 창 목록과 같은 항목에 대해 잘 작동 합니다.<br /><br /> 유효 기간: `Button`|
|DynamicVisibility|메서드를 통해 `QueryStatus` 또는 섹션에 포함 된 컨텍스트 GUID를 통해 명령의 표시 유형을 변경할 수 있습니다 `VisibilityConstraints` .<br /><br /> 메뉴 및 도구 창 도구 모음에 표시 되는 명령에 적용 되지만 주 창에 표시 되는 최상위 도구 모음에는 적용 되지 않습니다. 메서드에서 OLECMDF_INVISIBLE 플래그가 반환 될 때 최상위 도구 모음 항목은 사용 하지 않도록 설정할 수 있지만 숨길 수는 없습니다 `QueryStatus` . 도구 창 도구 모음에 표시 되는 도구 모음 명령은 숨길 수 있습니다.<br /><br /> 메뉴에서이 플래그는 모든 멤버가 숨겨진 경우에도 자동으로 숨겨지도록 함을 나타냅니다. 최상위 메뉴에는이 동작이 이미 있으므로이 플래그는 일반적으로 하위 메뉴에 할당 됩니다.<br /><br /> 이 플래그는 플래그와 함께 사용 해야 합니다 `DefaultInvisible` .<br /><br /> 유효 기간: `Button` , `Combo` , `Menu`|
|기능의|[콤보 요소](../extensibility/combo-element.md)에서 필터링 키 항목을 참조 하세요.<br /><br /> 유효 기간: `Combo`|
|FixMenuController|이 명령이 메뉴 컨트롤러에 배치 되는 경우 명령은 항상 기본값입니다. 즉, 메뉴 컨트롤러 단추 자체를 선택할 때마다 명령이 선택 됩니다. 메뉴 컨트롤러에 `TextIsAnchorCommand` 플래그가 설정 되어 있으면 메뉴 컨트롤러도 플래그를 포함 하는 명령에서 텍스트를 가져옵니다 `FixMenuController` .<br /><br /> 메뉴 컨트롤러에서 하나의 명령만 플래그를 포함 해야 합니다 `FixMenuController` . 둘 이상의 명령이 표시 되는 경우 메뉴의 마지막 명령이 기본 명령이 됩니다.<br /><br /> 유효 기간: `Button`|
|IconAndText|메뉴와 도구 모음에 아이콘과 텍스트를 표시 합니다.<br /><br /> 유효 기간: `Button` , `Combo` , `Menu`|
|NoAutoComplete 완성|자동 완성 기능을 사용할 수 없습니다.<br /><br /> 유효 기간: `Combo`|
|NoButtonCustomize 지정|사용자가이 단추를 사용자 지정할 수 없도록 합니다.<br /><br /> 유효 기간: `Button` , `Combo`|
|NoKeyCustomize|키보드 사용자 지정을 사용 하지 마십시오.<br /><br /> 유효 기간: `Button` , `Combo`|
|NoShowOnMenuController|이 명령을 메뉴 컨트롤러에 배치 하면 명령이 드롭다운 목록에 나타나지 않습니다.<br /><br /> 유효 기간: `Button`|
|NotInTBList|사용 가능한 도구 모음 목록에 표시 되지 않습니다. 이는 도구 모음 메뉴 유형에만 사용할 수 있습니다.<br /><br /> 유효 기간: `Menu`|
|Noa를 닫습니다.|사용자가 도구 모음을 닫을 수 없습니다. 이는 도구 모음 메뉴 유형에만 사용할 수 있습니다.<br /><br /> 유효 기간: `Menu`|
|최적화|메뉴의 텍스트만 표시 하 고 도구 모음에는 아이콘만 표시 합니다. 아이콘을 지정 하지 않으면 도구 모음에서 클릭 가능한 빈 공간을 표시 합니다.<br /><br /> 유효 기간: `Button`|
|PostExec|명령이 차단 되지 않는 것으로 만듭니다. 개발 환경은 모든 전처리 쿼리가 완료 될 때까지 실행을 지연 합니다.<br /><br /> 유효 기간: `Button`|
|RouteToDocs|명령이 활성 문서로 라우팅됩니다.<br /><br /> 유효 기간: `Button`|
|StretchHorizontally|이 플래그를 설정 하면 너비가 콤보 상자의 최소 너비가 되며 도구 모음에 공간이 있으면 콤보 상자가 확장 되어 사용 가능한 공간을 채웁니다. 이는 도구 모음이 가로로 도킹 된 경우에만 발생 하 고 도구 모음의 콤보 상자 하나만 플래그를 사용할 수 있습니다 (첫 번째 콤보 상자를 제외한 모든 항목에서 플래그가 무시 됨).<br /><br /> 유효 기간: `Combo`|
|TextChanges|명령 또는 메뉴 텍스트는 런타임에 일반적으로 메서드를 통해 변경할 수 있습니다 `QueryStatus` .<br /><br /> 유효 기간: `Button` , `Menu`|
|Text[단추]|유효 기간: `Button`|
|TextIsAnchorCommand|메뉴 컨트롤러의 경우 기본 (앵커) 명령에서 메뉴의 텍스트를 가져옵니다. 앵커 명령은 마지막으로 선택 되거나 걸려 있는 명령입니다. 이 플래그를 설정 하지 않으면 메뉴 컨트롤러는 자체 필드를 사용 합니다 `MenuText` . 그러나 메뉴 컨트롤러를 클릭 해도 해당 컨트롤러에서 마지막으로 선택한 명령이 활성화 됩니다.<br /><br /> 플래그와이 플래그를 결합 하는 것이 좋습니다 `TextChanges` .<br /><br /> 이 플래그는 메뉴 메뉴에만 적용 됩니다 메뉴 메뉴에는 MenuController 또는 래치 합니다.<br /><br /> 유효 기간: `Menu`|
|TextMenuCtrlUseMenu|`MenuText`메뉴 컨트롤러의 필드를 사용 합니다. 기본 필드는 `ButtonText` 입니다.<br /><br /> 유효 기간: `Button`|
|TextMenuUseButton|`ButtonText`메뉴에 필드를 사용 합니다. 기본 필드는 `MenuText` 지정 된 경우입니다.<br /><br /> 유효 기간: `Button`|
|TextOnly|아이콘이 지정 된 경우에도 도구 모음 또는 메뉴에 텍스트를 표시 하지만 아이콘은 표시 하지 않습니다.<br /><br /> 유효 기간: `Button`|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Buttons 요소](../extensibility/buttons-element.md)|[단추 요소](../extensibility/button-element.md) 요소에 대 한 그룹을 제공 합니다.|
|[Menus 요소](../extensibility/menus-element.md)|VSPackage가 구현 하는 모든 메뉴를 정의 합니다.|

## <a name="see-also"></a>참고 항목
- [Visual Studio 명령 테이블 (. Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

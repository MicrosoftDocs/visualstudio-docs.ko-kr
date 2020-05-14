---
title: 명령 플래그 요소 | 마이크로 소프트 문서
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
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649366"
---
# <a name="command-flag-eelement"></a>명령 플래그 Eelement
상위 요소를 수정합니다.

## <a name="syntax"></a>구문

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 유효한 요소 값을 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소

|값|설명|
|-----------|-----------------|
|허용파라름|사용자가 **명령의** 표준 이름을 입력할 때 명령 창에 명령 매개 변수를 입력할 수 있음을 나타냅니다.<br /><br /> 유효 하다:`Button`|
|항상 만들기|메뉴는 그룹이나 단추가 없는 경우에도 만들어집니다.<br /><br /> 유효 하다:`Menu`|
|CaseSensitive|사용자 항목은 대/소문자를 구분합니다.<br /><br /> 유효 하다:`Combo`|
|커맨드웰만|명령이 최상위 메뉴에 나타나지 않고 추가 셸 사용자 지정(예: 키보드 단축큰 가기)에 사용할 수 있도록 하려는 경우 이 플래그를 적용합니다. VSPackage를 설치한 후 **옵션** 대화 상자를 연 다음 **키보드 환경** 범주에서 명령 배치를 편집하여 이러한 명령을 사용자 지정할 수 있습니다. 이 플래그는 바로 가기 메뉴, 도구 모음, 메뉴 컨트롤러 또는 하위 메뉴의 배치에는 영향을 주지 않습니다.<br /><br /> 에 대 `Button`한 유효한:`Combo`|
|기본 장애인|기본적으로 이를 구현하는 VSPackage가 로드되지 않았거나 메서드가 호출되지 `QueryStatus` 않은 경우 명령이 비활성화됩니다.<br /><br /> 에 대 `Button`한 유효한:`Combo`|
|기본도킹|기본적으로 도킹됩니다. 이 설정은 항상 도킹되어 있으므로 도구 모음에 더 이상 적용되지 않습니다.|
|기본값 보이지 않음|기본적으로 이를 구현하는 VSPackage가 로드되지 않았거나 메서드가 `QueryStatus` 호출되지 않은 경우 명령이 표시되지 않습니다.<br /><br /> 플래그와 `DynamicVisibility` 결합하는 것이 좋습니다.<br /><br /> 에 대 `Button` `Combo`한 유효한: "`Menu`|
|돈트캐시|개발 환경은 이 `QueryStatus` 명령에 대한 메서드 결과를 캐시하지 않습니다.<br /><br /> 메뉴의 경우 메뉴 컨트롤러가 메뉴 항목의 텍스트를 캐시하지 않도록 지시합니다. 메뉴에 동적 텍스트가 있는 동적 항목 또는 항목이 포함된 경우 이 플래그를 사용합니다.<br /><br /> 에 대 `Button`한 유효한:`Menu`|
|동적 항목 시작|동적 목록의 시작을 나타냅니다. 이렇게 하면 OLECMDERR_E_UNSUPPORTED 플래그가 반환될 때까지 `QueryStatus` 목록 항목의 메서드를 연속적으로 호출하여 목록을 작성할 수 있습니다. 가장 최근에 사용한(MRU) 목록 및 창 목록과 같은 항목에 적합합니다.<br /><br /> 유효 하다:`Button`|
|동적 가시성|명령의 가시성은 메서드를 `QueryStatus` 통해 또는 섹션에 포함된 컨텍스트 GUID를 `VisibilityConstraints` 통해 변경할 수 있습니다.<br /><br /> 메뉴 및 도구 창 도구 모음에는 표시되지만 기본 창에 표시되는 최상위 도구 모음에는 표시되지 않는 명령에 적용됩니다. 최상위 도구 모음 항목은 `QueryStatus` 메서드에서 OLECMDF_INVISIBLE 플래그가 반환될 때 사용하지 않도록 설정하지만 숨길 수 없습니다. 도구 창 도구 모음에 나타나는 도구 모음 명령을 숨길 수 있습니다.<br /><br /> 메뉴에서 이 플래그는 모든 멤버가 숨겨져 있을 때 자동으로 숨어져야 한다는 것을 나타냅니다. 최상위 메뉴에 이 동작이 이미 있기 때문에 이 플래그는 일반적으로 하위 메뉴에 할당됩니다.<br /><br /> 이 플래그는 `DefaultInvisible` 플래그와 결합되어야 합니다.<br /><br /> 에 대 `Button` `Combo`한 유효한: "`Menu`|
|필터 키|[콤보 요소](../extensibility/combo-element.md)에서 필터링 키 항목을 참조하십시오.<br /><br /> 유효 하다:`Combo`|
|픽스메뉴컨트롤러|이 명령이 메뉴 컨트롤러에 배치된 경우 명령은 항상 기본값입니다. 즉, 메뉴 컨트롤러 단추 자체를 선택할 때마다 명령이 선택됩니다. 메뉴 컨트롤러에 플래그가 `TextIsAnchorCommand` 설정된 경우 메뉴 컨트롤러는 `FixMenuController` 플래그가 있는 명령에서 텍스트를 가져갑니다.<br /><br /> 메뉴 컨트롤러의 명령에는 플래그가 `FixMenuController` 하나만 있어야 합니다. 두 개 이상의 명령이 표시되면 메뉴의 마지막 명령이 기본 명령이 됩니다.<br /><br /> 유효 하다:`Button`|
|아이콘및텍스트|메뉴 및 도구 모음에 아이콘과 텍스트를 표시합니다.<br /><br /> 에 대 `Button` `Combo`한 유효한: "`Menu`|
|자동 완성없음|자동 완성 기능이 비활성화되어 있습니다.<br /><br /> 유효 하다:`Combo`|
|버튼 없음 사용자 지정|사용자가 이 단추를 사용자 지정하지 않도록 합니다.<br /><br /> 에 대 `Button`한 유효한:`Combo`|
|아니오키커스터마이즈|키보드 사용자 지정을 사용하지 마십시오.<br /><br /> 에 대 `Button`한 유효한:`Combo`|
|노쇼온메뉴컨트롤러|이 명령이 메뉴 컨트롤러에 배치되면 드롭다운 목록에 명령이 나타나지 않습니다.<br /><br /> 유효 하다:`Button`|
|노인TB리스트|사용 가능한 도구 모음 목록에 나타나지 않습니다. 도구 모음 메뉴 유형에만 유효합니다.<br /><br /> 유효 하다:`Menu`|
|노툴바닫기|사용자가 도구 모음을 닫을 수 없습니다. 도구 모음 메뉴 유형에만 유효합니다.<br /><br /> 유효 하다:`Menu`|
|Pict|도구 모음에는 아이콘만 표시하지만 메뉴에는 텍스트만 표시합니다. 아이콘을 지정하지 않으면 도구 모음에 클릭 가능한 빈 공간이 표시됩니다.<br /><br /> 유효 하다:`Button`|
|포스트엑섹|명령을 비차단합니다. 개발 환경은 모든 사전 처리 쿼리가 완료될 때까지 실행을 연기합니다.<br /><br /> 유효 하다:`Button`|
|루트토독스|명령이 활성 문서로 라우팅됩니다.<br /><br /> 유효 하다:`Button`|
|늘이기수평|이 플래그를 설정하면 너비가 콤보 상자의 최소 너비가 되고 도구 모음에 공간이 있으면 콤보 상자가 늘어나 사용 가능한 공간을 채웁니다. 이 문제는 도구 모음이 수평으로 도킹되어 있고 도구 모음의 하나의 콤보 상자만 플래그를 사용할 수 있는 경우에만 발생합니다(첫 번째 콤보 상자를 제외한 모든 경우 플래그는 무시됨).<br /><br /> 유효 하다:`Combo`|
|텍스트 변경|명령 또는 메뉴 텍스트는 일반적으로 메서드를 `QueryStatus` 통해 런타임에 변경할 수 있습니다.<br /><br /> 에 대 `Button`한 유효한:`Menu`|
|텍스트 변경 버튼|유효 하다:`Button`|
|텍스트Is앵커명령|메뉴 컨트롤러의 경우 메뉴 텍스트는 기본(앵커) 명령에서 가져온 것입니다. 앵커 명령은 선택또는 래치된 마지막 명령입니다. 이 플래그가 설정되지 않은 경우 메뉴 `MenuText` 컨트롤러는 자체 필드를 사용합니다. 그러나 메뉴 컨트롤러를 클릭하면 해당 컨트롤러에서 마지막으로 선택한 명령을 사용할 수 있습니다.<br /><br /> 이 플래그를 플래그와 결합하는 `TextChanges` 것이 좋습니다.<br /><br /> 이 플래그는 메뉴컨트롤러 또는 MenuControllerLatched 형식의 메뉴에만 적용됩니다.<br /><br /> 유효 하다:`Menu`|
|텍스트메뉴CtrluseMenu|메뉴 `MenuText` 컨트롤러의 필드를 사용합니다. 기본 필드는 `ButtonText`.<br /><br /> 유효 하다:`Button`|
|텍스트 메뉴사용 버튼|메뉴에 `ButtonText` 필드를 사용합니다. 기본 필드는 `MenuText` 지정된 경우입니다.<br /><br /> 유효 하다:`Button`|
|텍스트 만|도구 모음이나 메뉴에는 텍스트만 표시되지만 아이콘이 지정된 경우에도 아이콘은 표시되지 않습니다.<br /><br /> 유효 하다:`Button`|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[단추 요소](../extensibility/buttons-element.md)|[단추 요소](../extensibility/button-element.md) 요소에 대한 그룹을 제공합니다.|
|[메뉴 요소](../extensibility/menus-element.md)|VSPackage가 구현하는 모든 메뉴를 정의합니다.|

## <a name="see-also"></a>참고 항목
- [비주얼 스튜디오 명령 테이블(. Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

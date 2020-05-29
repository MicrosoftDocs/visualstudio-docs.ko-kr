---
title: 만들. Vsct 파일 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f02c7ec0e453f0758ba2ab13145fcdff11b442a
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173605"
---
# <a name="author-vsct-files"></a>. Vsct 파일 작성
이 문서에서는 Visual Studio IDE (통합 개발 환경)에 메뉴 항목, 도구 모음 및 기타 UI (사용자 인터페이스) 요소를 추가 하기 위해 *vsct* 파일을 작성 하는 방법을 보여 줍니다. VSPackage (Visual Studio 패키지)에 이미 *. vsct* 파일이 없는 UI 요소를 추가할 때 이러한 단계를 사용 합니다.

 새 프로젝트의 경우 선택한 항목에 따라 메뉴 명령, 도구 창 또는 사용자 지정 편집기에 대 한 필수 요소가 이미 있는 *vsct* 파일을 생성 하기 때문에 Visual Studio 패키지 템플릿을 사용 하는 것이 좋습니다. VSPackage 요구 사항에 맞게이 *vsct* 파일을 수정할 수 있습니다. *. Vsct* 파일을 수정 하는 방법에 대 한 자세한 내용은 [메뉴 및 명령 확장](../../extensibility/extending-menus-and-commands.md)의 예제를 참조 하세요.

## <a name="author-the-file"></a>파일 작성
 이러한 단계에서 *. vsct* 파일을 작성 합니다. 파일 및 리소스에 대 한 구조를 만들고, ui 요소를 선언 하 고, ui 요소를 IDE에 배치 하 고, 특수 동작을 추가 합니다.

### <a name="file-structure"></a>파일 구조
 *. Vsct* 파일의 기본 구조는 [명령](../../extensibility/commands-element.md) 요소 및 [기호](../../extensibility/symbols-element.md) 요소를 포함 하는 [commandtable](../../extensibility/commandtable-element.md) root 요소입니다.

#### <a name="to-create-the-file-structure"></a>파일 구조를 만들려면

1. [방법: vsct 파일 만들기](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)의 단계를 수행 하 *여 파일을* 프로젝트에 추가 합니다.

2. 다음 예제와 같이 필수 네임 스페이스를 요소에 추가 합니다 `CommandTable` .

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. 요소에 `CommandTable` 요소를 추가 `Commands` 하 여 모든 사용자 지정 메뉴, 도구 모음, 명령 그룹 및 명령을 호스팅합니다. 사용자 지정 UI 요소를 로드할 수 있도록 `Commands` 요소의 `Package` 특성이 패키지 이름으로 설정 되어 있어야 합니다.

     요소 뒤에 `Commands` 요소를 추가 `Symbols` 하 여 패키지에 대 한 GUID 및 UI 요소에 대 한 이름 및 명령 id를 정의 합니다.

### <a name="include-visual-studio-resources"></a>Visual Studio 리소스 포함
 [Extern](../../extensibility/extern-element.md) 요소를 사용 하 여 IDE에서 UI 요소를 배치 하는 데 필요한 Visual Studio 명령 및 메뉴를 정의 하는 파일에 액세스 합니다. 패키지 외부에 정의 된 명령을 사용 하는 경우 [UsedCommands](../../extensibility/usedcommands-element.md) 요소를 사용 하 여 Visual Studio에 알립니다.

#### <a name="to-include-visual-studio-resources"></a>Visual Studio 리소스를 포함 하려면

1. 요소의 맨 위에서 `CommandTable` `Extern` 참조할 각 외부 파일에 대해 하나의 요소를 추가 하 고 `href` 특성을 파일 이름으로 설정 합니다. 다음 헤더 파일을 참조 하 여 Visual Studio 리소스에 액세스할 수 있습니다.

   - *Stdidcmd*: Visual Studio에서 노출 하는 모든 명령의 id를 정의 합니다.

   - *Vsshlids .h*: Visual Studio 메뉴에 대 한 명령 id를 포함 합니다.

2. 패키지에서 Visual Studio 또는 다른 패키지에 정의 된 명령을 호출 하는 경우 요소 뒤에 요소를 추가 `UsedCommands` `Commands` 합니다. 이 요소를 패키지의 일부가 아닌 호출 하는 각 명령에 대 한 [UsedCommand](../../extensibility/usedcommand-element.md) 요소로 채웁니다. `guid` `id` 요소의 및 특성을 `UsedCommand` 호출할 명령의 GUID 및 ID 값으로 설정 합니다.

   Visual Studio 명령의 Guid 및 Id를 찾는 방법에 대 한 자세한 내용은 [Visual studio 명령의 guid 및 id](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)를 참조 하세요. 다른 패키지에서 명령을 호출 하려면 해당 패키지에 대 한 *vsct* 파일에 정의 된 대로 명령의 GUID 및 ID를 사용 합니다.

### <a name="declare-ui-elements"></a>UI 요소 선언
 `Symbols` *. Vsct* 파일의 섹션에서 모든 새 UI 요소를 선언 합니다.

#### <a name="to-declare-ui-elements"></a>UI 요소를 선언 하려면

1. 요소에 `Symbols` 세 개의 [GuidSymbol](../../extensibility/guidsymbol-element.md) 요소를 추가 합니다. 각 `GuidSymbol` 요소에는 `name` 특성과 `value` 특성이 있습니다. `name`요소의 용도를 반영 하도록 특성을 설정 합니다. `value`특성은 GUID를 사용 합니다. (GUID를 생성 하려면 **도구** 메뉴에서 **guid 만들기**를 선택 하 고 **레지스트리 형식**을 선택 합니다.)

     첫 번째 `GuidSymbol` 요소는 패키지를 나타내고 일반적으로 자식이 없습니다. 두 번째 `GuidSymbol` 요소는 명령 집합을 나타내며 메뉴, 그룹 및 명령을 정의 하는 모든 기호를 포함 합니다. 세 번째 `GuidSymbol` 요소는 이미지 저장소를 나타내며 명령의 모든 아이콘에 대 한 기호를 포함 합니다. 아이콘을 사용 하는 명령이 없으면 세 번째 요소를 생략할 수 있습니다 `GuidSymbol` .

2. `GuidSymbol`명령 집합을 나타내는 요소에서 하나 이상의 [idsymbol](../../extensibility/idsymbol-element.md) 요소를 추가 합니다. 각각은 UI에 추가 하는 메뉴, 도구 모음, 그룹 또는 명령을 나타냅니다.

     각 요소에 대해 `IDSymbol` `name` 해당 메뉴, 그룹 또는 명령을 참조 하는 데 사용할 이름으로 특성을 설정 하 고 `value` 해당 명령 ID를 나타내는 16 진수 값으로 요소를 설정 합니다. `IDSymbol`부모가 동일한 두 요소는 동일한 값을 가질 수 없습니다.

3. UI 요소에 아이콘이 필요한 경우 `IDSymbol` 이미지 저장소를 나타내는 요소에 각 아이콘의 요소를 추가 `GuidSymbol` 합니다.

### <a name="put-ui-elements-in-the-ide"></a>IDE에서 UI 요소를 배치 합니다.
 [메뉴](../../extensibility/menus-element.md), [그룹](../../extensibility/groups-element.md)및 [단추](../../extensibility/buttons-element.md) 요소에는 패키지에 정의 된 모든 메뉴, 그룹 및 명령에 대 한 정의가 포함 되어 있습니다. UI 요소 정의의 일부인 [부모](../../extensibility/parent-element.md) 요소를 사용 하거나 다른 곳에서 정의 된 [commandplacement](../../extensibility/commandplacement-element.md) 요소를 사용 하 여 IDE에 이러한 메뉴, 그룹 및 명령을 배치 합니다.

 각 `Menu` , `Group` 및 `Button` 요소에는 `guid` 특성과 `id` 특성이 있습니다. 항상 특성을 `guid` `GuidSymbol` 명령 집합을 나타내는 요소의 이름과 일치 하도록 설정 하 고, 특성을 `id` `IDSymbol` 섹션의 메뉴, 그룹 또는 명령을 나타내는 요소의 이름으로 설정 합니다 `Symbols` .

#### <a name="to-define-ui-elements"></a>UI 요소를 정의 하려면

1. 새 메뉴, 하위 메뉴, 바로 가기 메뉴 또는 도구 모음을 정의 하는 경우 요소를 `Menus` 요소에 추가 `Commands` 합니다. 그런 다음 생성 될 각 메뉴에 대 한 [메뉴](../../extensibility/menu-element.md) 요소를 요소에 추가 `Menus` 합니다.

    `guid` `id` 요소의 및 특성을 설정 하 `Menu` 고 `type` 특성을 원하는 메뉴 종류로 설정 합니다. `priority`부모 그룹에서 메뉴의 상대 위치를 설정 하도록 특성을 설정할 수도 있습니다.

   > [!NOTE]
   > `priority`특성은 도구 모음 및 상황에 맞는 메뉴에는 적용 되지 않습니다.

2. Visual Studio IDE의 모든 명령은 메뉴와 도구 모음의 직계 자식인 명령 그룹에서 호스팅해야 합니다. IDE에 새 메뉴 또는 도구 모음을 추가 하는 경우 새 명령 그룹을 포함 해야 합니다. 명령을 시각적으로 그룹화 할 수 있도록 기존 메뉴와 도구 모음에 명령 그룹을 추가할 수도 있습니다.

    새 명령 그룹을 추가 하는 경우 먼저 요소를 만든 `Groups` 다음 각 명령 그룹에 대 한 [그룹](../../extensibility/group-element.md) 요소를 추가 해야 합니다.

    `guid` `id` 각 요소의 및 특성을 설정 하 `Group` 고 특성을 설정 `priority` 하 여 부모 메뉴에서 그룹의 상대 위치를 설정 합니다. 자세한 내용은 [다시 사용할 수 있는 단추 그룹 만들기](../../extensibility/creating-reusable-groups-of-buttons.md)를 참조 하세요.

3. IDE에 새 명령을 추가 하는 경우 요소를 `Buttons` 요소에 추가 `Commands` 합니다. 그런 다음 각 명령에 대해 요소에 [Button](../../extensibility/button-element.md) 요소를 추가 `Buttons` 합니다.

   1. `guid` `id` 각 요소의 및 특성을 설정 하 `Button` 고 특성을 `type` 원하는 단추의 종류로 설정 합니다. `priority`부모 그룹에서 명령의 상대 위치를 설정 하도록 특성을 설정할 수도 있습니다.

       > [!NOTE]
       > `type="button"`도구 모음에서 표준 메뉴 명령 및 단추를 사용 합니다.

   2. 요소에 `Button` [buttontext](../../extensibility/buttontext-element.md) 요소와 [CommandName](../../extensibility/commandname-element.md) 요소가 포함 된 [Strings](../../extensibility/strings-element.md) 요소를 추가 합니다. `ButtonText`요소는 메뉴 항목에 대 한 텍스트 레이블이나 도구 모음 단추에 대 한 도구 설명을 제공 합니다. `CommandName`요소는 명령 웰에서 사용할 명령의 이름을 제공 합니다.

   3. 명령에 아이콘이 있는 경우 요소에 [아이콘](../../extensibility/icon-element.md) 요소를 만들고 `Button` 해당 `guid` 및 `id` 특성을 `Bitmap` 아이콘의 요소로 설정 합니다.

       > [!NOTE]
       > 도구 모음 단추에는 아이콘이 있어야 합니다.

   자세한 내용은 [Menucommands 및 OleMenuCommands](/visualstudio/misc/menucommands-vs-olemenucommands?view=vs-2015)를 참조 하세요.

4. 명령에 아이콘이 필요한 경우 요소에 [비트맵](../../extensibility/bitmaps-element.md) 요소를 추가 `Commands` 합니다. 그런 다음 각 아이콘에 대해 [비트맵](../../extensibility/bitmap-element.md) 요소를 요소에 추가 `Bitmaps` 합니다. 여기서는 비트맵 리소스의 위치를 지정 합니다. 자세한 내용은 [메뉴 명령에 아이콘 추가](../../extensibility/adding-icons-to-menu-commands.md)를 참조 하세요.

   부모 구조체를 사용 하 여 대부분의 메뉴, 그룹 및 명령을 올바르게 지정할 수 있습니다. 매우 큰 명령 집합의 경우 또는 메뉴, 그룹 또는 명령이 여러 위치에 표시 되어야 하는 경우 명령 배치를 지정 하는 것이 좋습니다.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>부모를 사용 하 여 IDE에 UI 요소를 추가 하려면

1. 일반적인 부모로는 `Parent` `Menu` `Group` 패키지에 정의 된 각, 및 요소에 요소를 만듭니다 `Command` .

    `Parent`요소의 대상은 메뉴, 그룹 또는 명령을 포함 하는 메뉴 또는 그룹입니다.

   1. 특성을 `guid` `GuidSymbol` 명령 집합을 정의 하는 요소의 이름으로 설정 합니다. 대상 요소가 패키지의 일부가 아닌 경우 해당 하는 *vsct* 파일에 정의 된 대로 해당 명령 집합의 guid를 사용 합니다.

   2. 특성을 `id` `id` 대상 메뉴 또는 그룹의 특성과 일치 하도록 설정 합니다. Visual Studio에서 노출 하는 메뉴 및 그룹의 목록은 visual studio [메뉴의 guid 및 id](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) [및 visual Studio 도구 모음의 guid 및 id](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)를 참조 하세요.

   IDE에 포함할 UI 요소가 많은 경우 또는 여러 위치에 표시 되어야 하는 요소가 있는 경우 다음 단계에 표시 된 것 처럼 [commandplacements](../../extensibility/commandplacements-element.md) 요소에서 배치를 정의 합니다.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>명령 배치를 사용 하 여 UI 요소를 IDE에 배치 하려면

1. `Commands` 요소 다음에 `CommandPlacements` 요소를 추가합니다.

2. 요소에 `CommandPlacements` `CommandPlacement` 각 메뉴, 그룹 또는 명령에 대 한 요소를 추가 합니다.

    각 `CommandPlacement` 요소 또는 `Parent` 요소는 하나의 IDE 위치에 하나의 메뉴, 그룹 또는 명령을 배치 합니다. UI 요소에는 하나의 부모만 있을 수 있지만 여러 개의 명령 배치가 있을 수 있습니다. UI 요소를 여러 위치에 배치 하려면 `CommandPlacement` 각 위치에 대해 요소를 추가 합니다.

3. `guid` `id` `CommandPlacement` 요소와 마찬가지로 각 요소의 및 특성을 호스팅 메뉴 또는 그룹으로 설정 합니다 `Parent` . 특성을 설정 하 여 `priority` UI 요소의 상대 위치를 설정할 수도 있습니다.

   배치를 부모로 하 고 명령 배치를 혼합할 수 있습니다. 그러나 매우 큰 명령 집합의 경우 명령 배치만 사용 하는 것이 좋습니다.

### <a name="add-specialized-behaviors"></a>특수 동작 추가
 [Commandflag](../../extensibility/command-flag-element.md) 요소를 사용 하 여 메뉴 및 명령의 동작을 수정할 수 있습니다. 예를 들어 모양 및 표시 유형을 변경할 수 있습니다. [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) 요소를 사용 하 여 명령을 볼 때 또는 [KeyBindings](../../extensibility/keybindings-element.md) 요소를 사용 하 여 바로 가기 키를 추가 하는 경우에도 영향을 줄 수 있습니다. 특정 종류의 메뉴 및 명령에는 이미 특수 한 동작이 내장 되어 있습니다.

#### <a name="to-add-specialized-behaviors"></a>특수 동작을 추가 하려면

1. 솔루션이 로드 되는 경우와 같이 특정 UI 컨텍스트에서만 UI 요소를 표시 하려면 표시 유형 제약 조건을 사용 합니다.

   1. `Commands` 요소 다음에 `VisibilityConstraints` 요소를 추가합니다.

   2. 제한할 각 UI 항목에 대해 [VisibilityItem](../../extensibility/visibilityitem-element.md) 요소를 추가 합니다.

   3. 각 요소에 대해 `VisibilityItem` `guid` 및 특성을 `id` 메뉴, 그룹 또는 명령으로 설정한 다음 `context` 클래스에 정의 된 대로 특성을 원하는 UI 컨텍스트로 설정 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> .

2. 코드에서 UI 항목의 표시 여부를 설정 하려면 다음 명령 플래그 중 하나 이상을 사용 합니다.

   - `DefaultDisabled`

   - `DefaultInvisible`

   - `DynamicItemStart`

   - `DynamicVisibility`

   - `NoShowOnMenuController`

   - `NotInTBList`

   자세한 내용은 [Commandflag](../../extensibility/command-flag-element.md) 요소를 참조 하세요.

3. 요소가 표시 되는 방식을 변경 하거나 동적으로 모양을 변경 하려면 다음 명령 플래그 중 하나 이상을 사용 합니다.

   - `AlwaysCreate`

   - `CommandWellOnly`

   - `DefaultDocked`

   - `DontCache`

   - `DynamicItemStart`

   - `FixMenuController`

   - `IconAndText`

   - `Pict`

   - `StretchHorizontally`

   - `TextMenuUseButton`

   - `TextChanges`

   - `TextOnly`

   자세한 내용은 [Commandflag](../../extensibility/command-flag-element.md) 요소를 참조 하세요.

4. 명령을 받을 때 요소가 반응 하는 방식을 변경 하려면 다음 명령 플래그 중 하나 이상을 사용 합니다.

   - `AllowParams`

   - `CaseSensitive`

   - `CommandWellOnly`

   - `FilterKeys`

   - `NoAutoComplete`

   - `NoButtonCustomize`

   - `NoKeyCustomize`

   - `NoToolbarClose`

   - `PostExec`

   - `RouteToDocs`

   - `TextIsAnchorCommand`

   자세한 내용은 [Commandflag](../../extensibility/command-flag-element.md) 요소를 참조 하세요.

5. 메뉴 또는 메뉴의 항목에 메뉴 종속 바로 가기 키를 연결 하려면 `ButtonText` 메뉴 또는 메뉴 항목에 대 한 요소에 앰퍼샌드 문자 (&)를 추가 합니다. 앰퍼샌드 다음에 오는 문자는 부모 메뉴가 열릴 때 활성 키보드 바로 가기입니다.

6. 명령에 메뉴 독립적인 바로 가기 키를 연결 하려면 키 [바인딩](../../extensibility/keybindings-element.md) 요소를 사용 합니다. 자세한 내용은 [KeyBinding](../../extensibility/keybinding-element.md) 요소를 참조 하세요.

7. 메뉴 텍스트를 지역화 하려면 요소를 사용 `LocCanonicalName` 합니다. 자세한 내용은 [Strings](../../extensibility/strings-element.md) 요소를 참조 하세요.

   일부 메뉴 및 단추 형식에는 특수 동작이 포함 되어 있습니다. 다음 목록에서는 특수 메뉴 및 단추 형식에 대해 설명 합니다. 다른 형식에 대해서는 `types` [메뉴](../../extensibility/menu-element.md), [단추](../../extensibility/button-element.md)및 [콤보](../../extensibility/combo-element.md) 요소에서 특성 설명을 참조 하십시오.

   - 콤보 상자: 콤보 상자는 도구 모음에서 사용할 수 있는 드롭다운 목록입니다. UI에 콤보 상자를 추가 하려면 요소에 [Combos](../../extensibility/combos-element.md) 요소를 만듭니다 `Commands` . 그런 다음 `Combos` `Combo` 추가할 각 콤보 상자에 대 한 요소를 요소에 추가 합니다. `Combo`요소는 요소와 동일한 특성 및 자식을 가지 `Button` 며 `DefaultWidth` 및 특성도 포함 `idCommandList` 합니다. `DefaultWidth`특성은 너비를 픽셀 단위로 설정 하 고, `idCommandList` 특성은 콤보 상자를 채우는 데 사용 되는 명령 ID를 가리킵니다.

   - 메뉴 컨트롤러: 메뉴 컨트롤러는 옆에 화살표를 포함 하는 단추입니다. 화살표를 클릭 하면 목록이 열립니다. 메뉴 컨트롤러를 UI에 추가 하려면 `Menu` `type` `MenuController` 원하는 동작에 따라 요소를 만들고 해당 특성을 or로 설정 `MenuControllerLatched` 합니다. 메뉴 컨트롤러를 채우려면 요소의 부모로 설정 `Group` 합니다. 메뉴 컨트롤러는 드롭다운 목록에서 해당 그룹의 모든 자식을 표시 합니다.

## <a name="see-also"></a>참고 항목
- [메뉴 및 명령 확장](../../extensibility/extending-menus-and-commands.md)
- [Visual Studio 명령 테이블 (.vvsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)

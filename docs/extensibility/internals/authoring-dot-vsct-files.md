---
title: 제작. Vsct 파일 | 마이크로 소프트 문서
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
ms.openlocfilehash: dfa276d04e2d312d7ff00b1e9bc0015beb1e254e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709990"
---
# <a name="author-vsct-files"></a>작성자 .vsct 파일
이 문서에서는 *.vsct* 파일을 작성하여 메뉴 항목, 도구 모음 및 기타 사용자 인터페이스(UI) 요소를 IDE(Visual Studio 통합 개발 환경)에 추가하는 방법을 보여 줍니다. *.vsct* 파일이 아직 없는 VSPackage(Visual Studio 패키지)에 UI 요소를 추가할 때 다음 단계를 사용합니다.

 새 프로젝트의 경우 선택 항목에 따라 메뉴 명령, 도구 창 또는 사용자 지정 편집기에 필요한 요소가 이미 있는 *.vsct* 파일을 생성하기 때문에 Visual Studio 패키지 템플릿을 사용하는 것이 좋습니다. VSPackage의 요구 사항을 충족하도록 이 *.vsct* 파일을 수정할 수 있습니다. *.vsct* 파일을 수정하는 방법에 대한 자세한 내용은 [확장 메뉴 및 명령의 예제를](../../extensibility/extending-menus-and-commands.md)참조하십시오.

## <a name="author-the-file"></a>파일 작성
 다음 단계에서 *.vsct* 파일 작성: 파일 및 리소스에 대한 구조를 만들고, UI 요소를 선언하고, UI 요소를 IDE에 넣고, 특수한 동작을 추가합니다.

### <a name="file-structure"></a>파일 구조
 *.vsct* 파일의 기본 구조는 [명령](../../extensibility/commands-element.md) 요소와 [기호](../../extensibility/symbols-element.md) 요소를 포함하는 [CommandTable](../../extensibility/commandtable-element.md) 루트 요소입니다.

#### <a name="to-create-the-file-structure"></a>파일 구조를 만들려면

1. *.vsct* 파일 만들기 방법의 단계를 수행하여 프로젝트에 [.vsct 파일을 추가합니다.](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

2. 다음 예제와 같이 `CommandTable` 요소에 필요한 네임스페이스를 추가합니다.

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. `CommandTable` 요소에서 `Commands` 요소를 추가하여 모든 사용자 지정 메뉴, 도구 모음, 명령 그룹 및 명령을 호스트합니다. 사용자 지정 UI 요소를 로드할 `Commands` 수 있도록 `Package` 요소에 패키지 이름으로 설정된 특성이 있어야 합니다.

     `Commands` 요소 후 `Symbols` 패키지에 대 한 GUID를 정의 하는 요소를 추가 하 고 UI 요소에 대 한 이름 및 명령 ID를 지정 합니다.

### <a name="include-visual-studio-resources"></a>비주얼 스튜디오 리소스 포함
 [Extern](../../extensibility/extern-element.md) 요소를 사용하여 Visual Studio 명령을 정의하는 파일과 UI 요소를 IDE에 넣는 데 필요한 메뉴에 액세스합니다. 패키지 외부에 정의된 명령을 사용하는 경우 [UsedCommands](../../extensibility/usedcommands-element.md) 요소를 사용하여 Visual Studio에 알립니다.

#### <a name="to-include-visual-studio-resources"></a>비주얼 스튜디오 리소스를 포함하려면

1. `CommandTable` 요소의 맨 위에 참조할 `Extern` 각 외부 파일에 대해 하나의 요소를 `href` 추가하고 파일 이름으로 특성을 설정합니다. 다음 헤더 파일을 참조하여 Visual Studio 리소스에 액세스할 수 있습니다.

   - *Stdidcmd.h*: Visual Studio에서 노출하는 모든 명령에 대한 암호를 정의합니다.

   - *Vsshlids.h*: 비주얼 스튜디오 메뉴에 대한 명령 아이디를 포함합니다.

2. 패키지가 Visual Studio 또는 다른 패키지에서 정의한 명령을 호출하는 `UsedCommands` 경우 `Commands` 요소 다음의 요소를 추가합니다. 이 요소를 패키지의 일부가 아닌 호출하는 각 명령에 대해 [UsedCommand](../../extensibility/usedcommand-element.md) 요소로 채웁니다. 호출할 `guid` `id` 명령의 GUID 및 ID 값에 요소의 및 특성을 설정합니다. `UsedCommand`

   Visual Studio 명령의 GUID 및 이의를 찾는 방법에 대한 자세한 내용은 [Visual Studio 명령의 GUID 및 ID를](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)참조하십시오. 다른 패키지의 명령을 호출하려면 해당 패키지에 대해 *.vsct* 파일에 정의된 명령의 GUID 및 ID를 사용합니다.

### <a name="declare-ui-elements"></a>UI 요소 선언
 `Symbols` *.vsct* 파일 섹션의 모든 새 UI 요소를 선언합니다.

#### <a name="to-declare-ui-elements"></a>UI 요소를 선언하려면

1. 요소에서 `Symbols` 세 개의 GuidSymbol 요소를 [추가합니다.](../../extensibility/guidsymbol-element.md) 각 `GuidSymbol` 요소에는 `name` 특성과 `value` 특성이 있습니다. 요소의 `name` 용도를 반영하도록 특성을 설정합니다. 특성은 `value` GUID를 취합니다. (GUID를 생성하려면 **도구** 메뉴에서 **GUID 만들기를**선택한 다음 **레지스트리 형식을**선택합니다.)

     첫 `GuidSymbol` 번째 요소는 패키지를 나타내며 일반적으로 자식이 없습니다. 두 `GuidSymbol` 번째 요소는 명령 집합을 나타내며 메뉴, 그룹 및 명령을 정의하는 모든 기호를 포함합니다. 세 `GuidSymbol` 번째 요소는 이미지 저장소를 나타내며 명령의 모든 아이콘에 대한 기호를 포함합니다. 아이콘을 사용하는 명령이 없는 경우 세 번째 `GuidSymbol` 요소를 생략할 수 있습니다.

2. 명령 `GuidSymbol` 집합을 나타내는 요소에서 하나 이상의 [IDSymbol](../../extensibility/idsymbol-element.md) 요소를 추가합니다. 이들 각각은 UI에 추가하는 메뉴, 도구 모음, 그룹 또는 명령을 나타냅니다.

     각 `IDSymbol` 요소에 대해 `name` 해당 메뉴, 그룹 또는 명령을 참조하는 데 사용할 이름으로 특성을 `value` 설정한 다음 요소를 명령 ID를 나타내는 헥사드피말 번호로 설정합니다. 부모가 `IDSymbol` 동일한 두 요소는 동일한 값을 가질 수 없습니다.

3. UI 요소에 아이콘이 필요한 경우 이미지 `IDSymbol` 저장소를 나타내는 `GuidSymbol` 요소에 각 아이콘에 대한 요소를 추가합니다.

### <a name="put-ui-elements-in-the-ide"></a>IDE에 UI 요소 넣기
 [메뉴,](../../extensibility/menus-element.md) [그룹](../../extensibility/groups-element.md)및 [단추](../../extensibility/buttons-element.md) 요소에는 패키지에 정의된 모든 메뉴, 그룹 및 명령에 대한 정의가 포함됩니다. UI 요소 정의의 일부인 [부모](../../extensibility/parent-element.md) 요소를 사용하거나 다른 위치에 정의된 [CommandPlacement](../../extensibility/commandplacement-element.md) 요소를 사용하여 IDE에 이러한 메뉴, 그룹 및 명령을 넣습니다.

 각 `Menu` `Group`및 `Button` 요소에는 `guid` 특성과 `id` 특성이 있습니다. 항상 명령 `guid` 집합을 `GuidSymbol` 나타내는 요소의 이름과 `id` 일치하도록 특성을 설정하고 섹션에서 메뉴, `IDSymbol` 그룹 또는 명령을 나타내는 요소의 `Symbols` 이름으로 특성을 설정합니다.

#### <a name="to-define-ui-elements"></a>UI 요소를 정의하려면

1. 새 메뉴, 하위 메뉴, 바로 가기 메뉴 또는 도구 모음을 정의하는 `Menus` 경우 `Commands` 요소에 요소를 추가합니다. 그런 다음 각 메뉴를 만들려면 [Menu](../../extensibility/menu-element.md) `Menus` 요소에 메뉴 요소를 추가합니다.

    요소의 `guid` `id` 및 특성을 설정한 다음 `type` 속성을 원하는 메뉴 의 종류로 설정합니다. `Menu` 부모 그룹에서 메뉴의 상대적 위치를 설정하도록 `priority` 특성을 설정할 수도 있습니다.

   > [!NOTE]
   > 이 `priority` 특성은 도구 모음 및 컨텍스트 메뉴에는 적용되지 않습니다.

2. Visual Studio IDE의 모든 명령은 메뉴 및 도구 모음의 직접 자식인 명령 그룹에서 호스팅해야 합니다. IDE에 새 메뉴 나 도구 모음을 추가하는 경우 새 명령 그룹이 포함되어야 합니다. 명령을 시각적으로 그룹화할 수 있도록 기존 메뉴 및 도구 모음에 명령 그룹을 추가할 수도 있습니다.

    새 명령 그룹을 추가할 때 먼저 `Groups` 요소를 만든 다음 각 명령 그룹에 대한 [그룹](../../extensibility/group-element.md) 요소를 추가해야 합니다.

    각 `Group` `guid` 요소의 및 `id` 특성을 설정한 다음 `priority` 특성을 설정하여 상위 메뉴에서 그룹의 상대적 위치를 설정합니다. 자세한 내용은 [재사용 가능한 단추 그룹 만들기를](../../extensibility/creating-reusable-groups-of-buttons.md)참조하십시오.

3. IDE에 새 명령을 추가하는 경우 `Buttons` `Commands` 요소에 요소를 추가합니다. 그런 다음 각 명령에 대해 [요소에](../../extensibility/button-element.md) `Buttons` Button 요소를 추가합니다.

   1. 각 `Button` `guid` 요소의 및 `id` 특성을 설정한 다음 `type` 속성을 원하는 단추 의 종류로 설정합니다. 부모 그룹에서 명령의 상대적 위치를 설정하도록 `priority` 특성을 설정할 수도 있습니다.

       > [!NOTE]
       > 도구 `type="button"` 모음의 표준 메뉴 명령 및 단추에 사용합니다.

   2. `Button` 요소에서 [ButtonText](../../extensibility/buttontext-element.md) 요소와 [CommandName](../../extensibility/commandname-element.md) 요소를 포함하는 [문자열](../../extensibility/strings-element.md) 요소를 추가합니다. 요소는 `ButtonText` 메뉴 항목에 대한 텍스트 레이블 또는 도구 모음 단추의 도구 설명을 제공합니다. 요소는 `CommandName` 명령에서 사용할 명령의 이름을 잘 제공합니다.

   3. 명령에 아이콘이 있는 경우 `Button` 요소에 [아이콘](../../extensibility/icon-element.md) 요소를 만들고 아이콘의 `guid` `id` `Bitmap` 요소에 아이콘및 속성을 설정합니다.

       > [!NOTE]
       > 도구 모음 단추에는 아이콘이 있어야 합니다.

   자세한 내용은 [메뉴 명령 및 올레메뉴 명령 서를 참조하십시오.](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015)

4. 명령에 아이콘이 필요한 경우 `Commands` 요소에 [비트맵](../../extensibility/bitmaps-element.md) 요소를 추가합니다. 그런 다음 각 아이콘에 대해 요소에 `Bitmaps` [비트맵](../../extensibility/bitmap-element.md) 요소를 추가합니다. 여기서 비트맵 리소스의 위치를 지정합니다. 자세한 내용은 [메뉴 명령에 아이콘 추가 를](../../extensibility/adding-icons-to-menu-commands.md)참조하십시오.

   대부분의 메뉴, 그룹 및 명령을 올바르게 배치하려면 부모 구성에 의존할 수 있습니다. 매우 큰 명령 집합의 경우 또는 메뉴, 그룹 또는 명령이 여러 위치에 나타나야 하는 경우 명령 배치를 지정하는 것이 좋습니다.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>IDE에 UI 요소를 배치하기 위해 육아에 의존하려면

1. 일반적인 육아의 경우 `Parent` 패키지에 `Menu` `Group`정의된 `Command` 각 . 및 요소에 요소를 만듭니다.

    `Parent` 요소의 대상은 메뉴, 그룹 또는 명령을 포함하는 메뉴 또는 그룹입니다.

   1. 명령 `guid` 집합을 정의하는 `GuidSymbol` 요소의 이름으로 특성을 설정합니다. 대상 요소가 패키지의 일부가 아닌 경우 해당 *.vsct* 파일에 정의된 대로 해당 명령 집합에 대한 guid를 사용합니다.

   2. 특성을 `id` 대상 메뉴 `id` 또는 그룹의 특성과 일치하도록 설정합니다. Visual Studio에서 노출되는 메뉴 및 그룹의 목록은 Visual Studio 메뉴 또는 GUID 및 Visual [Studio 도구 모음의 GUID 및 GUID 및 ID를](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)참조하십시오. [GUIDs and IDs of Visual Studio menus](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

   IDE에 배치할 UI 요소가 많거나 여러 위치에 나타나야 하는 요소가 있는 경우 다음 단계에 표시된 대로 [CommandPlacements](../../extensibility/commandplacements-element.md) 요소에서 해당 위치를 정의합니다.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>명령 배치를 사용하여 IDE에 UI 요소를 배치하려면

1. `Commands` 요소 다음에 `CommandPlacements` 요소를 추가합니다.

2. `CommandPlacements` 요소에서 배치할 `CommandPlacement` 각 메뉴, 그룹 또는 명령에 대한 요소를 추가합니다.

    각 `CommandPlacement` 요소 `Parent` 또는 요소는 하나의 IDE 위치에 하나의 메뉴, 그룹 또는 명령을 배치합니다. UI 요소에는 하나의 부모만 있을 수 있지만 여러 명령 배치가 있을 수 있습니다. UI 요소를 여러 위치에 배치하려면 `CommandPlacement` 각 위치에 대한 요소를 추가합니다.

3. `Parent` 각 `CommandPlacement` `guid` 요소의 및 `id` 속성을 요소와 마찬가지로 호스팅 메뉴 또는 그룹에 설정합니다. UI 요소의 `priority` 상대위치를 설정하기 위해 특성을 설정할 수도 있습니다.

   육아 및 명령 배치를 통해 배치를 혼합할 수 있습니다. 그러나 매우 큰 명령 집합의 경우 명령 배치만 사용하는 것이 좋습니다.

### <a name="add-specialized-behaviors"></a>특수 동작 추가
 [CommandFlag](../../extensibility/command-flag-element.md) 요소를 사용하여 메뉴 및 명령의 동작을 수정할 수 있습니다(예: 모양 및 가시성 변경). [또한 가시성 제약](../../extensibility/visibilityconstraints-element.md) 요소를 사용하여 명령을 볼 수 있는 경우에 영향을 주거나 [KeyBindings](../../extensibility/keybindings-element.md) 요소를 사용하여 바로 가기 키를 추가할 수도 있습니다. 특정 종류의 메뉴와 명령에는 이미 특수 동작이 내장되어 있습니다.

#### <a name="to-add-specialized-behaviors"></a>특수 동작을 추가하려면

1. 예를 들어 솔루션이 로드될 때 와 같은 특정 UI 컨텍스트에서만 UI 요소를 표시하려면 가시성 제약 조건을 사용합니다.

   1. `Commands` 요소 다음에 `VisibilityConstraints` 요소를 추가합니다.

   2. 구속할 각 UI 항목에 대해 가시성항목 요소를 [추가합니다.](../../extensibility/visibilityitem-element.md)

   3. 각 `VisibilityItem` 요소에 대해 `guid` 및 `id` 특성을 메뉴, 그룹 또는 명령으로 설정한 `context` 다음 클래스에 정의된 대로 원하는 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> UI 컨텍스트로 특성을 설정합니다.

2. 코드에서 UI 항목의 가시성 또는 가용성을 설정하려면 다음 명령 플래그 중 하나 이상을 사용합니다.

   - `DefaultDisabled`

   - `DefaultInvisible`

   - `DynamicItemStart`

   - `DynamicVisibility`

   - `NoShowOnMenuController`

   - `NotInTBList`

   자세한 내용은 [CommandFlag](../../extensibility/command-flag-element.md) 요소를 참조하십시오.

3. 요소가 나타나는 방식을 변경하거나 모양을 동적으로 변경하려면 다음 명령 플래그 중 하나 이상을 사용합니다.

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

   자세한 내용은 [CommandFlag](../../extensibility/command-flag-element.md) 요소를 참조하십시오.

4. 명령이 수신될 때 요소가 반응하는 방식을 변경하려면 다음 명령 플래그 중 하나 이상을 사용합니다.

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

   자세한 내용은 [CommandFlag](../../extensibility/command-flag-element.md) 요소를 참조하십시오.

5. 메뉴에 따라 달라붙은 키보드 단축기를 메뉴 또는 메뉴의 항목에 연결하려면 메뉴 또는 `ButtonText` 메뉴 항목의 요소에 앰퍼샌드 문자(&)를 추가합니다. ampersand 다음에 오는 문자는 부모 메뉴가 열려 있을 때 활성 키보드 바로 가기입니다.

6. 메뉴 독립적인 키보드 단축키를 명령에 첨부하려면 [KeyBindings](../../extensibility/keybindings-element.md) 요소를 사용합니다. 자세한 내용은 [KeyBinding](../../extensibility/keybinding-element.md) 요소를 참조하십시오.

7. 메뉴 텍스트를 지역화하려면 `LocCanonicalName` 요소를 사용합니다. 자세한 내용은 [문자열](../../extensibility/strings-element.md) 요소를 참조하십시오.

   일부 메뉴 및 단추 유형에는 특수 동작이 포함됩니다. 다음 목록에서는 몇 가지 특수 한 메뉴 및 단추 유형에 대해 설명 합니다. `types` 다른 형식의 경우 [메뉴,](../../extensibility/menu-element.md) [단추](../../extensibility/button-element.md)및 [콤보](../../extensibility/combo-element.md) 요소의 특성 설명을 참조하세요.

   - 콤보 상자: 콤보 상자는 도구 모음에서 사용할 수 있는 드롭다운 목록입니다. UI에 콤보 상자를 추가하려면 `Commands` 요소에 [콤보](../../extensibility/combos-element.md) 요소를 만듭니다. 그런 다음 `Combos` 각 `Combo` 콤보 상자에 대한 요소를 요소에 추가하여 추가할 수 있습니다. `Combo`요소는 `Button` 요소와 동일한 특성 및 자식을 `idCommandList` 가지며 또한 속성과 특성을 가짐을 가짐입니다. `DefaultWidth` 속성은 `DefaultWidth` 너비를 픽셀 단위로 설정하고 `idCommandList` 특성은 콤보 상자를 채우는 데 사용되는 명령 ID를 가리킵니다.

   - 메뉴 컨트롤러: 메뉴 컨트롤러옆에 화살표가 있는 버튼입니다. 화살표를 클릭하면 목록이 열립니다. UI에 메뉴 컨트롤러를 추가하려면 `Menu` 요소를 만들고 `type` 원하는 `MenuController` 동작에 따라 해당 특성을 또는 `MenuControllerLatched`에 설정합니다. 메뉴 컨트롤러를 채우려면 `Group` 요소의 부모로 설정합니다. 메뉴 컨트롤러는 해당 그룹의 모든 자식을 드롭다운 목록에 표시합니다.

## <a name="see-also"></a>참조
- [메뉴 및 명령 확장](../../extensibility/extending-menus-and-commands.md)
- [비주얼 스튜디오 명령 테이블 (.vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)

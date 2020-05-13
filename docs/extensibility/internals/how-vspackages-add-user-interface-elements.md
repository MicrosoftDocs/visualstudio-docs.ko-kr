---
title: VSPackage사용자 인터페이스 요소를 추가하는 방법 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d9cc3184009dd98e743064db1b8eb2abe6059d1
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649592"
---
# <a name="how-vspackages-add-user-interface-elements"></a>VSPackage사용자 인터페이스 요소를 추가하는 방법
VSPackage는 *.vsct* 파일을 사용하여 메뉴, 도구 모음 및 도구 창과 같은 사용자 인터페이스(UI) 요소를 Visual Studio에 추가할 수 있습니다.

[Visual Studio 사용자 환경 지침에서](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)UI 요소에 대한 디자인 지침을 찾을 수 있습니다.

## <a name="the-visual-studio-command-table-architecture"></a>비주얼 스튜디오 명령 테이블 아키텍처
언급했듯이 명령 테이블 아키텍처는 설명된 아키텍처 원칙을 지원합니다. 명령 테이블 아키텍처의 추상화, 데이터 구조 및 도구 뒤에 있는 신조는 다음과 같습니다.

- 항목에는 메뉴, 명령 및 그룹의 세 가지 기본 종류가 있습니다. 메뉴는 UI에서 메뉴, 하위 메뉴, 도구 모음 또는 도구 창으로 노출될 수 있습니다. 명령은 사용자가 IDE에서 실행할 수 있는 프로시저이며 메뉴 항목, 단추, 목록 상자 또는 기타 컨트롤로 노출될 수 있습니다. 그룹은 메뉴와 명령에 대한 컨테이너입니다.

- 각 항목은 항목을 설명하는 정의, 다른 항목에 대한 우선 순위 및 해당 동작을 수정하는 플래그에 의해 지정됩니다.

- 각 항목에는 항목의 상위를 설명하는 게재위치가 있습니다. 항목에는 여러 부모가 있을 수 있으므로 UI의 여러 위치에 표시될 수 있습니다.

모든 명령은 해당 그룹의 유일한 자식인 경우에도 그룹을 상위 그룹으로 가져야 합니다. 모든 표준 메뉴에는 상위 그룹도 있어야 합니다. 도구 모음 및 도구 창은 자체 부모 역할을 합니다. 그룹은 주 Visual Studio 메뉴 모음 또는 메뉴, 도구 모음 또는 도구 창을 부모로 가질 수 있습니다.

### <a name="how-items-are-defined"></a>항목 정의 방법
*.vsct* 파일은 XML로 서식이 지정됩니다. 패키지에 대한 UI 요소를 정의하고 이러한 요소가 IDE에 표시되는 위치를 결정합니다. 패키지의 모든 메뉴, 그룹 또는 명령은 먼저 섹션에 `Symbols` GUID 및 ID가 할당됩니다. *.vsct* 파일의 나머지 부분에서 각 메뉴, 명령 및 그룹은 GUID 및 ID 조합으로 식별됩니다. 다음 예제에서는 메뉴 `Symbols` **명령이 템플릿에서** 선택될 때 Visual Studio 패키지 템플릿에서 생성된 일반적인 섹션을 보여 줍니다.

```xml
<Symbols>
  <!-- This is the package guid. -->
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />

  <!-- This is the guid used to group the menu commands together -->
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">
    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
  </GuidSymbol>

  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}">
    <IDSymbol name="bmpPic1" value="1" />
    <IDSymbol name="bmpPic2" value="2" />
    <IDSymbol name="bmpPicSearch" value="3" />
    <IDSymbol name="bmpPicX" value="4" />
    <IDSymbol name="bmpPicArrows" value="5" />
  </GuidSymbol>
</Symbols>
```

`Symbols` 섹션의 최상위 요소는 [GuidSymbol 요소입니다.](../../extensibility/guidsymbol-element.md) `GuidSymbol`요소는 패키지 및 해당 구성 요소 부분을 식별하기 위해 IDE에서 사용하는 GUID에 이름을 매핑합니다.

> [!NOTE]
> GUID는 Visual Studio 패키지 템플릿에 의해 자동으로 생성됩니다. **도구** 메뉴에서 **GUID 만들기를** 클릭하여 고유한 GUID를 만들 수도 있습니다.

첫 `GuidSymbol` 번째 `guid<PackageName>Pkg`요소는 패키지 자체의 GUID입니다. 이 GUID는 Visual Studio에서 패키지를 로드하는 데 사용하는 GUID입니다. 일반적으로 자식 요소가 없습니다.

규칙에 `GuidSymbol` 따라 메뉴와 명령은 두 번째 요소 `guid<PackageName>CmdSet`아래에 그룹화되고 비트맵은 `GuidSymbol` 세 `guidImages`번째 요소 아래에 있습니다. 이 규칙을 따를 필요는 없지만 각 메뉴, 그룹, 명령 및 비트맵은 `GuidSymbol` 요소의 자식이어야 합니다.

패키지 명령 `GuidSymbol` 집합을 나타내는 두 번째 요소에는 여러 `IDSymbol` 요소가 있습니다. 각 [IDSymbol 요소는](../../extensibility/idsymbol-element.md) 이름을 숫자 값에 매핑하며 명령 집합의 일부인 메뉴, 그룹 또는 명령을 나타낼 수 있습니다. 세 `IDSymbol` 번째 `GuidSymbol` 요소의 요소는 명령의 아이콘으로 사용될 수 있는 비트맵을 나타냅니다. GUID/ID 쌍은 응용 프로그램에서 고유해야 하므로 동일한 `GuidSymbol` 요소의 두 자식이 동일한 값을 가질 수 없습니다.

### <a name="menus-groups-and-commands"></a>메뉴, 그룹 및 명령
메뉴, 그룹 또는 명령에 GUID 및 ID가 있는 경우 IDE에 추가할 수 있습니다. 모든 UI 요소에는 다음과 같은 사항이 있어야 합니다.

- UI `guid` `GuidSymbol` 요소가 아래에 정의된 요소의 이름과 일치하는 특성입니다.

- 연결된 `id` `IDSymbol` 요소의 이름과 일치하는 특성입니다.

및 특성은 함께 UI 요소의 서명을 구성합니다. *signature* `guid` `id`

- 상위 `priority` 메뉴 또는 그룹에서 UI 요소의 배치를 결정하는 특성입니다.

- 상위 메뉴 또는 `guid` `id` 그룹의 서명을 지정하는 특성이 있는 상위 [요소입니다.](../../extensibility/parent-element.md)

#### <a name="menus"></a>메뉴
각 메뉴는 `Menus` 섹션의 메뉴 [요소로](../../extensibility/menu-element.md) 정의됩니다. 메뉴에는 `guid`. `id`및 `priority` 특성 및 `Parent` 요소와 다음과 같은 추가 속성 및 자식이 있어야 합니다.

- 메뉴를 `type` 일종의 메뉴또는 도구 모음으로 IDE에 표시할지 여부를 지정하는 특성입니다.

- IDE의 메뉴 제목을 지정하는 [ButtonText 요소를](../../extensibility/buttontext-element.md)포함하는 [문자열 요소와](../../extensibility/strings-element.md) **메뉴에** 액세스하는 데 사용되는 이름을 지정하는 [CommandName 요소입니다.](../../extensibility/commandname-element.md)

- 선택적 플래그입니다. [CommandFlag 요소는](../../extensibility/command-flag-element.md) 메뉴 정의에 표시되어 IDE의 모양이나 동작을 변경할 수 있습니다.

도구 `Menu` 모음과 같은 도킹 가능한 요소가 아니면 모든 요소에 그룹이 상위 그룹이 있어야 합니다. 도킹 가능한 메뉴는 자체 부모입니다. 속성의 메뉴 및 값에 대한 자세한 내용은 메뉴 요소 설명서를 참조하십시오. [Menu element](../../extensibility/menu-element.md) `type`

다음 예제에서는 **도구** 메뉴 옆에 있는 Visual Studio 메뉴 모음에 나타나는 메뉴를 보여 줍니다.

```xml
<Menu guid="guidTopLevelMenuCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
  <Parent guid="guidSHLMainMenu" id="IDG_VS_MM_TOOLSADDINS" />
  <Strings>
    <ButtonText>TestMenu</ButtonText>
    <CommandName>TestMenu</CommandName>
  </Strings>
</Menu>
```

#### <a name="groups"></a>그룹
그룹은 `Groups` *.vsct* 파일의 섹션에 정의된 항목입니다. 그룹은 컨테이너일 뿐입니다. 메뉴의 구분선을 제외하고 는 IDE에 나타나지 않습니다. 따라서 [그룹 요소는](../../extensibility/group-element.md) 서명, 우선 순위 및 부모에 의해서만 정의됩니다.

그룹에는 메뉴, 다른 그룹 또는 자체가 부모로 있을 수 있습니다. 그러나 부모는 일반적으로 메뉴 또는 도구 모음입니다. 이전 예제의 메뉴는 `IDG_VS_MM_TOOLSADDINS` 그룹의 자식이며 해당 그룹은 Visual Studio 메뉴 모음의 자식입니다. 다음 예제의 그룹은 이전 예제의 메뉴하위그룹입니다.

```xml
<Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" priority="0x0600">
  <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>
</Group>
```

이 그룹에는 메뉴의 일부이므로 일반적으로 명령이 포함됩니다. 그러나 다른 메뉴도 포함될 수 있습니다. 다음은 예제와 같이 하위 메뉴가 정의되는 방법입니다.

```xml
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu" priority="0x0100" type="Menu">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>
  <Strings>
    <ButtonText>Sub Menu</ButtonText>
    <CommandName>Sub Menu</CommandName>
  </Strings>
</Menu>
```

#### <a name="commands"></a>명령
IDE에 제공되는 명령은 [Button 요소](../../extensibility/button-element.md) 또는 [콤보 요소로](../../extensibility/combo-element.md)정의됩니다. 메뉴 또는 도구 모음에 표시하려면 명령에 그룹이 상위 그룹이어야 합니다.

##### <a name="buttons"></a>단추
단추는 섹션에 `Buttons` 정의되어 있습니다. 사용자가 단일 명령을 실행하기 위해 클릭하는 모든 메뉴 항목, 단추 또는 기타 요소는 단추로 간주됩니다. 일부 단추 유형에는 목록 기능도 포함될 수 있습니다. 단추에는 메뉴에 있는 필수 및 선택적 특성이 동일하며 IDE의 단추를 나타내는 비트맵의 GUID 및 ID를 지정하는 [Icon 요소가](../../extensibility/icon-element.md) 있을 수도 있습니다. 단추 및 해당 특성에 대한 자세한 내용은 [Buttons 요소 설명서를](../../extensibility/buttons-element.md) 참조하십시오.

다음 예제의 단추는 이전 예제에서 그룹의 자식이며 해당 그룹의 상위 메뉴에 있는 메뉴 항목으로 IDE에 나타납니다.

```xml
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <Strings>
    <CommandName>cmdidTestCommand</CommandName>
    <ButtonText>Test Command</ButtonText>
  </Strings>
</Button>
```

##### <a name="combos"></a>콤보
콤보는 섹션에 `Combos` 정의되어 있습니다. 각 `Combo` 요소는 IDE의 드롭다운 목록 상자를 나타냅니다. 목록 상자는 콤보 특성값에 `type` 따라 사용자가 작성할 수도 또는 사용하지 않을 수도 있습니다. 콤보는 단추와 동일한 요소 및 동작을 가지며 다음과 같은 추가 특성을 가질 수도 있습니다.

- 픽셀 `defaultWidth` 너비를 지정하는 특성입니다.

- 목록 `idCommandList` 상자에 표시되는 항목을 포함하는 목록을 지정하는 특성입니다. 명령 목록은 콤보를 포함하는 `GuidSymbol` 동일한 노드에서 선언되어야 합니다.

다음 예제는 콤보 요소를 정의합니다.

```xml
<Combos>
  <Combo guid="guidFirstToolWinCmdSet"
         id="cmdidWindowsMediaFilename"
         priority="0x0100" type="DynamicCombo"
         idCommandList="cmdidWindowsMediaFilenameGetList"
         defaultWidth="130">
    <Parent guid="guidFirstToolWinCmdSet"
            id="ToolbarGroupID" />
    <CommandFlag>IconAndText</CommandFlag>
    <CommandFlag>CommandWellOnly</CommandFlag>
    <CommandFlag>StretchHorizontally</CommandFlag>
    <Strings>
      <CommandName>Filename</CommandName>
      <ButtonText>Enter a Filename</ButtonText>
    </Strings>
  </Combo>
</Combos>
```

##### <a name="bitmaps"></a>비트맵
아이콘과 함께 표시되는 명령에는 GUID 및 `Icon` ID를 사용하여 비트맵을 참조하는 요소가 포함되어야 합니다. 각 비트맵은 섹션의 `Bitmaps` [비트맵 요소로](../../extensibility/bitmap-element.md) 정의됩니다. `Bitmap` 정의에 필요한 유일한 특성은 `guid` `href`및 소스 파일을 가리키는 입니다. 원본 파일이 리소스 스트립인 경우 스트립에 사용 가능한 이미지를 나열하려면 **usedList** 특성도 필요합니다. 자세한 내용은 [비트맵 요소](../../extensibility/bitmap-element.md) 설명서를 참조하십시오.

### <a name="parenting"></a>육아
다음 규칙은 항목이 다른 항목을 부모로 호출하는 방법을 제어합니다.

|요소|명령 테이블의 이 섹션에 정의되어 있습니다.|포함될 수 있습니다(부모로서, 또는 `CommandPlacements` 섹션의 배치에 의해, 또는 둘 다)|포함될 수 있습니다(부모라고 함)|
|-------------| - | - | - |
|그룹|[그룹 요소,](../../extensibility/groups-element.md)IDE, 기타 VSPackage|메뉴, 그룹, 항목 자체|메뉴, 그룹 및 명령|
|메뉴|[메뉴 요소,](../../extensibility/menus-element.md)IDE, 기타 VSPackages|1 ~ *n* 그룹|0 ~ *n* 그룹|
|도구 모음|[메뉴 요소,](../../extensibility/menus-element.md)IDE, 기타 VSPackages|항목 자체|0 ~ *n* 그룹|
|메뉴 항목|[버튼 요소,](../../extensibility/buttons-element.md)IDE, 기타 VSPackage|1 ~ *n* 그룹, 항목 자체|-0 ~ *n* 그룹|
|단추|[버튼 요소,](../../extensibility/buttons-element.md)IDE, 기타 VSPackage|1 ~ *n* 그룹, 항목 자체||
|콤보|[콤보 요소,](../../extensibility/combos-element.md)IDE, 기타 VSPackages|1 ~ *n* 그룹, 항목 자체||

### <a name="menu-command-and-group-placement"></a>메뉴, 명령 및 그룹 배치
메뉴, 그룹 또는 명령은 IDE의 두 개 이상의 위치에 나타날 수 있습니다. 항목이 여러 위치에 표시되려면 명령에 배치 `CommandPlacements` [요소로](../../extensibility/commandplacement-element.md)섹션에 추가해야 합니다. 모든 메뉴, 그룹 또는 명령을 명령 배치로 추가할 수 있습니다. 그러나 도구 모음은 여러 컨텍스트에 민감한 위치에 나타날 수 없으므로 이러한 방식으로 배치할 수 없습니다.

명령 배치에는 `guid` `id`및 `priority` 특성이 있습니다. GUID와 ID는 배치된 항목의 ID와 일치해야 합니다. 특성은 `priority` 다른 항목과 관련하여 항목의 배치를 제어합니다. IDE가 동일한 우선 순위를 가진 두 개 이상의 항목을 병합하는 경우 IDE가 패키지를 빌드할 때마다 패키지 리소스가 동일한 순서로 읽히는 것을 보장하지 않기 때문에 배치가 정의되지 않습니다.

메뉴 또는 그룹이 여러 위치에 나타나면 해당 메뉴 또는 그룹의 모든 하위 그룹이 각 인스턴스에 표시됩니다.

## <a name="command-visibility-and-context"></a>가시성 및 컨텍스트 명령
여러 VSPackage를 설치하면 메뉴, 메뉴 항목 및 도구 모음이 많이 있으면 IDE가 복잡해질 수 있습니다. 이 문제를 방지하려면 가시성 제약 조건 및 명령 플래그를 사용하여 개별 UI 요소의 *가시성을 제어할* 수 있습니다.

### <a name="visibility-constraints"></a>가시성 제약 조건
가시성 제약 조건은 `VisibilityConstraints` 단면의 [가시성항목 요소로](../../extensibility/visibilityitem-element.md) 설정됩니다. 가시성 제약 조건은 대상 항목이 표시되는 특정 UI 컨텍스트를 정의합니다. 이 섹션에 포함된 메뉴 나 명령은 정의된 컨텍스트 중 하나가 활성 상태일 때만 표시됩니다. 이 섹션에서 메뉴 또는 명령을 참조하지 않으면 기본적으로 항상 표시됩니다. 이 섹션은 그룹에 는 적용되지 않습니다.

`VisibilityItem`요소에는 다음과 `guid` `id` `context`같은 세 가지 특성이 있어야 합니다. 특성은 `context` 대상 항목이 표시되는 시기를 지정하고 유효한 UI 컨텍스트를 해당 값으로 합니다. Visual Studio의 UI 컨텍스트 상수는 <xref:Microsoft.VisualStudio.VSConstants> 클래스의 멤버입니다. 모든 `VisibilityItem` 요소는 하나의 컨텍스트 값만 사용할 수 있습니다. 두 번째 컨텍스트를 적용하려면 `VisibilityItem` 다음 예제와 같이 동일한 항목을 가리키는 두 번째 요소를 만듭니다.

```xml
<VisibilityConstraints>
  <VisibilityItem guid="guidSolutionToolbarCmdSet"
        id="cmdidTestCmd"
        context="UICONTEXT_SolutionHasSingleProject" />
  <VisibilityItem guid="guidSolutionToolbarCmdSet"
        id="cmdidTestCmd"
        context="UICONTEXT_SolutionHasMultipleProjects" />
</VisibilityConstraints>
```

### <a name="command-flags"></a>명령 플래그
다음 명령 플래그는 적용되는 메뉴 및 명령의 표시 에 영향을 줄 수 있습니다.

`AlwaysCreate`메뉴는 그룹이나 단추가 없는 경우에도 만들어집니다.

유효 하다:`Menu`

`CommandWellOnly`최상위 메뉴에 명령이 나타나지 않고 추가 셸 사용자 지정(예: 키에 바인딩)에 사용할 수 있도록 하려는 경우 이 플래그를 적용합니다. VSPackage를 설치한 후 사용자는 **옵션** 대화 상자를 연 다음 **키보드 환경** 범주에서 명령 배치를 편집하여 이러한 명령을 사용자 지정할 수 있습니다. 바로 가기 메뉴, 도구 모음, 메뉴 컨트롤러 또는 하위 메뉴의 배치에는 영향을 주지 않습니다.

에 대 `Button`한 유효한:`Combo`

`DefaultDisabled`기본적으로 명령을 구현하는 VSPackage가 로드되지 않았거나 QueryStatus 메서드가 호출되지 않은 경우 명령이 비활성화됩니다.

에 대 `Button`한 유효한:`Combo`

`DefaultInvisible`기본적으로 명령을 구현하는 VSPackage가 로드되지 않았거나 QueryStatus 메서드가 호출되지 않은 경우 명령이 표시되지 않습니다.

`DynamicVisibility` 플래그와 결합해야합니다.

에 대 `Button` `Combo`한 유효한: "`Menu`

`DynamicVisibility`섹션에 포함된 `QueryStatus` 메서드 또는 컨텍스트 GUID를 사용하여 명령의 가시성을 `VisibilityConstraints` 변경할 수 있습니다.

도구 모음이 아닌 메뉴에 나타나는 명령에 적용됩니다. 최상위 도구 모음 항목은 `OLECMDF_INVISIBLE` `QueryStatus` 메서드에서 플래그가 반환될 때 숨길 수 있지만 숨길 수는 없습니다.

메뉴에서 이 플래그는 멤버가 숨겨져 있을 때 자동으로 숨어져야 한다는 것을 나타냅니다. 최상위 메뉴에 이 동작이 이미 있기 때문에 이 플래그는 일반적으로 하위 메뉴에 할당됩니다.

`DefaultInvisible` 플래그와 결합해야합니다.

에 대 `Button` `Combo`한 유효한: "`Menu`

`NoShowOnMenuController`이 플래그가 있는 명령이 메뉴 컨트롤러에 배치되면 드롭다운 목록에 명령이 나타나지 않습니다.

유효 하다:`Button`

명령 플래그에 대한 자세한 내용은 [CommandFlag 요소](../../extensibility/command-flag-element.md) 설명서를 참조하십시오.

#### <a name="general-requirements"></a>일반 요구 사항
명령을 표시하고 활성화하려면 다음 일련의 테스트를 통과해야 합니다.

- 명령이 올바르게 배치됩니다.

- 플래그가 `DefaultInvisible` 설정되지 않았습니다.

- 상위 메뉴 또는 도구 모음이 표시됩니다.

- [가시성 제약 요소](../../extensibility/visibilityconstraints-element.md) 섹션의 컨텍스트 항목으로 인해 명령이 표시되지 않습니다.

- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스를 구현하는 VSPackage 코드는 명령을 표시하고 활성화합니다. 어떤 인터페이스 코드도 이를 가로채서 작동하지 않았습니다.

- 사용자가 명령을 클릭하면 [라우팅 알고리즘에](../../extensibility/internals/command-routing-algorithm.md)설명된 프로시저가 적용됩니다.

## <a name="call-pre-defined-commands"></a>미리 정의된 명령 호출
[USEDCommands 요소를](../../extensibility/usedcommands-element.md) 사용하면 VSPackage가 다른 VSPackage 또는 IDE에서 제공하는 명령에 액세스할 수 있습니다. 이렇게 하려면 사용할 명령의 GUID와 ID가 있는 [UsedCommand 요소를](../../extensibility/usedcommand-element.md) 만듭니다. 이렇게 하면 현재 Visual Studio 구성의 일부가 아니더라도 Visual Studio에서 명령을 로드할 수 있습니다. 자세한 내용은 [UsedCommand 요소를](../../extensibility/usedcommand-element.md)참조하십시오.

## <a name="interface-element-appearance"></a>인터페이스 요소 모양
명령 요소를 선택하고 배치하는 고려 사항은 다음과 같습니다.

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]배치에 따라 다르게 나타나는 많은 UI 요소를 제공합니다.

- `DefaultInvisible` 플래그를 사용하여 정의되는 UI 요소는 <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> 메서드의 VSPackage 구현에 의해 표시되거나 섹션의 특정 UI 컨텍스트와 연결되지 않는 한 IDE에 `VisibilityConstraints` 표시되지 않습니다.

- 성공적으로 배치된 명령도 표시되지 않을 수 있습니다. 이는 IDE가 VSPackage가 구현한 인터페이스에 따라 일부 명령을 자동으로 숨기거나 표시하기 때문입니다. 예를 들어 VSPackage의 일부 빌드 인터페이스 구현으로 인해 빌드 관련 메뉴 항목이 자동으로 표시됩니다.

- UI 요소의 정의에 `CommandWellOnly` 플래그를 적용하면 사용자 지정만 명령을 추가할 수 있습니다.

- 명령은 IDE가 디자인 뷰에 있을 때 대화 상자가 표시되는 경우에만 특정 UI 컨텍스트에서만 사용할 수 있습니다.

- 특정 UI 요소를 IDE에 표시하려면 하나 이상의 인터페이스를 구현하거나 일부 코드를 작성해야 합니다.

## <a name="see-also"></a>참고 항목
- [메뉴 및 명령 확장](../../extensibility/extending-menus-and-commands.md)

---
title: Vspackage 사용자 인터페이스 요소를 추가 하는 방법 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
caps.latest.revision: 61
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 553c502c100cbb6ed4ae249096af408af14423b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843275"
---
# <a name="how-vspackages-add-user-interface-elements"></a>VSPackage에서 사용자 인터페이스 요소를 추가하는 방법
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage 파일을 사용 하 여 메뉴, 도구 모음 및 도구 창과 같은 UI (사용자 인터페이스) 요소를 Visual Studio에 추가할 수 있습니다.  
  
 [Visual Studio 사용자 환경 지침](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)에서 UI 요소에 대 한 디자인 지침을 찾을 수 있습니다.  
  
## <a name="the-visual-studio-command-table-architecture"></a>Visual Studio 명령 테이블 아키텍처  
 앞서 설명한 것 처럼 명령 테이블 아키텍처는 앞서 설명한 아키텍처 원칙을 지원 합니다. 다음은 개념, 데이터 구조 및 명령 테이블 아키텍처의 도구 뒤에 오는 것입니다.  
  
- 메뉴, 명령 및 그룹의 세 가지 기본 항목 종류가 있습니다. 메뉴는 UI에서 메뉴, 하위 메뉴, 도구 모음 또는 도구 창으로 노출 될 수 있습니다. 명령은 사용자가 IDE에서 실행할 수 있는 프로시저 이며 메뉴 항목, 단추, 목록 상자 또는 기타 컨트롤로 노출 될 수 있습니다. 그룹은 메뉴와 명령 둘 다에 대 한 컨테이너입니다.  
  
- 각 항목은 항목을 설명 하는 정의, 다른 항목에 상대적인 우선 순위 및 해당 동작을 수정 하는 플래그에 의해 지정 됩니다.  
  
- 각 항목에는 항목의 부모를 설명 하는 배치가 있습니다. 항목은 여러 부모를 가질 수 있으므로 UI의 여러 위치에 나타날 수 있습니다.  
  
     모든 명령에는 해당 그룹의 유일한 자식인 경우에도 그룹을 부모로 포함 해야 합니다. 모든 표준 메뉴에는 부모 그룹도 있어야 합니다. 도구 모음 및 도구 창은 고유한 부모 역할을 합니다. 그룹은 기본 Visual Studio 메뉴 모음이 나 메뉴, 도구 모음 또는 도구 창의 부모로 사용할 수 있습니다.  
  
### <a name="how-items-are-defined"></a>항목 정의 방법  
 . Vsct 파일은 XML로 형식이 지정 됩니다. . Vsct 파일은 패키지에 대 한 UI 요소를 정의 하 고 IDE에 이러한 요소가 표시 되는 위치를 결정 합니다. 패키지의 모든 메뉴, 그룹 또는 명령에는 먼저 섹션에서 GUID 및 ID가 할당 됩니다 `Symbols` . Vsct 파일의 나머지 부분에서 각 메뉴, 명령 및 그룹은 해당 GUID 및 ID 조합으로 식별 됩니다. 다음 예제에서는 `Symbols` 템플릿에서 **메뉴 명령을** 선택할 때 Visual Studio 패키지 템플릿에서 생성 되는 일반적인 섹션을 보여 줍니다.  
  
```xml  
<Symbols>  
  <!-- This is the package guid. -->  
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />  
  
  <!-- This is the guid used to group the menu commands together -->  
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">  
  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
  </GuidSymbol>  
  
  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}" >  
    <IDSymbol name="bmpPic1" value="1" />  
    <IDSymbol name="bmpPic2" value="2" />  
    <IDSymbol name="bmpPicSearch" value="3" />  
    <IDSymbol name="bmpPicX" value="4" />  
    <IDSymbol name="bmpPicArrows" value="5" />  
  </GuidSymbol>  
</Symbols>  
```  
  
 섹션의 최상위 요소는 `Symbols` [GuidSymbol 요소](../../extensibility/guidsymbol-element.md)입니다. `GuidSymbol` 요소는 IDE에서 패키지 및 해당 구성 요소 파트를 식별 하는 데 사용 하는 Guid에 이름을 매핑합니다.  
  
> [!NOTE]
> Guid는 Visual Studio 패키지 템플릿에서 자동으로 생성 됩니다. **도구** 메뉴에서 **guid 만들기** 를 클릭 하 여 고유한 guid를 만들 수도 있습니다.  
  
 첫 번째 `GuidSymbol` 요소인 "guid [PackageName] Pkg"는 패키지 자체의 guid입니다. Visual Studio에서 패키지를 로드 하는 데 사용 하는 GUID입니다. 일반적으로 자식 요소를 포함 하지 않습니다.  
  
 규칙에 따라 메뉴와 명령은 두 번째 `GuidSymbol` 요소인 "guid [PackageName] CmdSet"로 그룹화 되 고 비트맵은 세 번째 `GuidSymbol` 요소인 "guidImages" 아래에 있습니다. 이 규칙을 따르는 것은 아니지만 각 메뉴, 그룹, 명령 및 비트맵이 요소의 자식 이어야 합니다 `GuidSymbol` .  
  
 `GuidSymbol`패키지 명령 집합을 나타내는 두 번째 요소에서는 여러 `IDSymbol` 요소입니다. 각 [Idsymbol 요소](../../extensibility/idsymbol-element.md) 는 이름을 숫자 값에 매핑하고 명령 집합의 일부인 메뉴, 그룹 또는 명령을 나타낼 수 있습니다. `IDSymbol`세 번째 요소의 요소는 `GuidSymbol` 명령에 대 한 아이콘으로 사용할 수 있는 비트맵을 나타냅니다. GUID/ID 쌍은 응용 프로그램에서 고유 해야 하므로 동일한 요소의 두 자식은 `GuidSymbol` 동일한 값을 가질 수 없습니다.  
  
### <a name="menus-groups-and-commands"></a>메뉴, 그룹 및 명령  
 메뉴, 그룹 또는 명령에 GUID 및 ID가 있는 경우 IDE에 추가할 수 있습니다. 모든 UI 요소에는 다음 항목이 있어야 합니다.  
  
- `guid`UI 요소가 정의 된 요소 이름과 일치 하는 특성입니다 `GuidSymbol` .  
  
- `id`연결 된 요소의 이름과 일치 하는 특성입니다 `IDSymbol` .  
  
     `guid`및 특성은 모두 `id` UI 요소의 *서명을* 구성 합니다.  
  
- `priority`부모 메뉴 또는 그룹에서 UI 요소의 배치를 결정 하는 특성입니다.  
  
- [Parent Element](../../extensibility/parent-element.md) `guid` `id` 부모 메뉴 또는 그룹의 서명을 지정 하는 및 특성이 있는 부모 요소입니다.  
  
#### <a name="menus"></a>메뉴  
 각 메뉴는 섹션에서 [메뉴 요소로](../../extensibility/menu-element.md) 정의 됩니다 `Menus` . 메뉴에는 `guid` , `id` , 및 특성 및 요소가 있어야 하 고, `priority` `Parent` 다음과 같은 추가 특성 및 자식 항목도 필요 합니다.  
  
- `type`메뉴가 IDE에 메뉴의 종류 또는 도구 모음으로 표시 되어야 하는지 여부를 지정 하는 특성입니다.  
  
- IDE에서 메뉴의 제목을 지정 하는 [Buttontext 요소가](../../extensibility/buttontext-element.md)포함 된 [Strings 요소](../../extensibility/strings-element.md) 와 **명령** 창에서 메뉴에 액세스 하는 데 사용 되는 이름을 지정 하는 [CommandName 요소](../../extensibility/commandname-element.md)입니다.  
  
- 선택적 플래그입니다. [명령 플래그 요소](../../extensibility/command-flag-element.md) 는 메뉴 정의에 표시 되어 IDE에서 모양이 나 동작을 변경할 수 있습니다.  
  
  `Menu`도구 모음과 같은 도킹 가능한 요소가 아닌 경우 모든 요소에는 그룹이 부모로 포함 되어야 합니다. 도킹 가능한 메뉴는 자체 부모입니다. 특성의 메뉴 및 값에 대 한 자세한 내용은 `type` [메뉴 요소](../../extensibility/menu-element.md) 설명서를 참조 하세요.  
  
  다음 예제에서는 **도구** 메뉴 옆의 Visual Studio 메뉴 모음에 표시 되는 메뉴를 보여 줍니다.  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet"  
id="TopLevelMenu" priority="0x700" type="Menu">  
  <Parent guid="guidSHLMainMenu"  
          id="IDG_VS_MM_TOOLSADDINS" />  
  <Strings>  
    <ButtonText>TestMenu</ButtonText>  
    <CommandName>TestMenu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="groups"></a>그룹  
 그룹은 `Groups` . vsct 파일의 섹션에서 정의 되는 항목입니다. 그룹은 단순한 컨테이너입니다. 메뉴의 구분선을 제외 하 고는 IDE에 나타나지 않습니다. 따라서 [Group 요소](../../extensibility/group-element.md) 는 해당 서명, 우선 순위 및 부모로만 정의 됩니다.  
  
 그룹은 메뉴, 다른 그룹 또는 자신을 부모로 지정할 수 있습니다. 그러나 부모는 일반적으로 메뉴 또는 도구 모음입니다. 이전 예제에서 메뉴는 그룹의 자식 이며 `IDG_VS_MM_TOOLSADDINS` , 해당 그룹은 Visual Studio 메뉴 모음의 자식입니다. 다음 예의 그룹은 이전 예제에서 메뉴의 자식입니다.  
  
```  
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"  
priority="0x0600">  
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>  
 </Group>  
```  
  
 이 그룹은 메뉴의 일부 이기 때문에 일반적으로 명령을 포함 합니다. 그러나 다른 메뉴가 포함 될 수도 있습니다. 다음 예제와 같이 하위 메뉴가 정의 된 방법입니다.  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu"  
priority="0x0100" type="Menu">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>  
  <Strings>  
    <ButtonText>Sub Menu</ButtonText>  
    <CommandName>Sub Menu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="commands"></a>명령  
 IDE에 제공 되는 명령은 [단추 요소](../../extensibility/button-element.md) 또는 [콤보 요소로](../../extensibility/combo-element.md)정의 됩니다. 메뉴 또는 도구 모음에 표시 하려면 명령에 그룹을 부모로 포함 해야 합니다.  
  
##### <a name="buttons"></a>단추  
 단추는 섹션에서 정의 됩니다 `Buttons` . 사용자가 단일 명령을 실행 하기 위해 클릭 하는 모든 메뉴 항목, 단추 또는 기타 요소는 단추로 간주 됩니다. 일부 단추 형식에는 목록 기능이 포함 될 수도 있습니다. 단추는 메뉴에 포함 된 것과 동일한 필수 및 선택적 특성을 가지 며 IDE의 단추를 나타내는 비트맵의 GUID 및 ID를 지정 하는 [아이콘 요소](../../extensibility/icon-element.md) 를 포함할 수도 있습니다. 단추 및 해당 특성에 대 한 자세한 내용은 [Buttons 요소](../../extensibility/buttons-element.md) 설명서를 참조 하세요.  
  
 다음 예제의 단추는 이전 예제에서 그룹의 자식 이며 IDE에서 해당 그룹의 부모 메뉴에 있는 메뉴 항목으로 나타납니다.  
  
```  
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <Strings>  
    <CommandName>cmdidTestCommand</CommandName>  
    <ButtonText>Test Command</ButtonText>  
  </Strings>  
</Button>  
```  
  
##### <a name="combos"></a>Combos  
 Combos는 섹션에 정의 되어 있습니다 `Combos` . 각 `Combo` 요소는 IDE의 드롭다운 목록 상자를 나타냅니다. 콤보의 특성 값에 따라 사용자가 목록 상자를 쓸 수 있거나 쓸 수 없습니다 `type` . Combos에는 단추와 동일한 요소 및 동작이 있으며 다음과 같은 추가 특성도 있을 수 있습니다.  
  
- `defaultWidth`픽셀 너비를 지정 하는 특성입니다.  
  
- `idCommandList`목록 상자에 표시 되는 항목을 포함 하는 목록을 지정 하는 특성입니다. 명령 목록은 `GuidSymbol` 콤보를 포함 하는 동일한 노드에서 선언 해야 합니다.  
  
  다음 예제에서는 콤보 요소를 정의 합니다.  
  
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
 아이콘과 함께 표시 되는 명령에는 `Icon` GUID 및 ID를 사용 하 여 비트맵을 참조 하는 요소가 포함 되어야 합니다. 각 비트맵은 섹션에서 [Bitmap 요소로](../../extensibility/bitmap-element.md) 정의 됩니다 `Bitmaps` . 정의에서 유일 하 게 필요한 특성은 `Bitmap` `guid` `href` 원본 파일을 가리키는 및입니다. 원본 파일이 리소스 스트립 인 경우 스트립에서 사용 가능한 이미지를 나열 하려면 **usedList** 특성도 필요 합니다. 자세한 내용은 [Bitmap 요소](../../extensibility/bitmap-element.md) 설명서를 참조 하세요.  
  
### <a name="parenting"></a>상위  
 다음 규칙은 항목이 다른 항목을 부모로 호출할 수 있는 방법을 제어 합니다.  
  
|요소|명령 테이블의이 섹션에 정의 된|포함 될 수 있습니다 (부모 또는 섹션의 배치로 또는 `CommandPlacements` 둘 다).|(부모 라고 함)를 포함할 수 있습니다.|  
|-------------|--------------------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------|  
|그룹|[Groups 요소](../../extensibility/groups-element.md), IDE, 기타 vspackage|메뉴, 그룹, 항목 자체|메뉴, 그룹 및 명령|  
|메뉴|[메뉴 요소](../../extensibility/menus-element.md), IDE, 기타 vspackage|1 ~ *n* 그룹|0- *n* 그룹|  
|도구 모음|[메뉴 요소](../../extensibility/menus-element.md), IDE, 기타 vspackage|항목 자체|0- *n* 그룹|  
|메뉴 항목|[Buttons 요소](../../extensibility/buttons-element.md), IDE, 기타 vspackage|1 ~ *n* 개의 그룹, 항목 자체|-0 ~ *n* 그룹|  
|단추|[Buttons 요소](../../extensibility/buttons-element.md), IDE, 기타 vspackage|1 ~ *n* 개의 그룹, 항목 자체||  
|콤보|[Combos 요소](../../extensibility/combos-element.md), IDE, 기타 vspackage|1 ~ *n* 개의 그룹, 항목 자체||  
  
### <a name="menu-command-and-group-placement"></a>메뉴, 명령 및 그룹 배치  
 메뉴, 그룹 또는 명령은 IDE의 여러 위치에 나타날 수 있습니다. 항목이 여러 위치에 표시 되려면 `CommandPlacements` [Commandplacement 요소로](../../extensibility/commandplacement-element.md)섹션에 추가 해야 합니다. 모든 메뉴, 그룹 또는 명령을 명령 배치로 추가할 수 있습니다. 그러나 도구 모음은 여러 상황에 맞는 위치에 표시 되지 않기 때문에 이런 방식으로 배치할 수 없습니다.  
  
 명령 배치에는 `guid` , `id` 및 `priority` 특성이 있습니다. GUID 및 ID는 배치 된 항목의 ID와 일치 해야 합니다. `priority`특성은 다른 항목과 관련 하 여 항목의 배치를 제어 합니다. IDE에서 우선 순위가 같은 두 개 이상의 항목을 병합 하는 경우 패키지를 빌드할 때마다 동일한 순서로 패키지 리소스를 읽도록 보장 하지 않기 때문에 해당 위치는 정의 되지 않습니다.  
  
 메뉴 또는 그룹이 여러 위치에 표시 되 면 해당 메뉴 또는 그룹의 모든 자식이 각 인스턴스에 표시 됩니다.  
  
## <a name="command-visibility-and-context"></a>명령 표시 유형 및 컨텍스트  
 여러 Vspackage가 설치 되 면 메뉴, 메뉴 항목 및 도구 모음의 다양 IDE가 간단해 집니다. 이 문제를 방지 하려면 *표시 유형 제약 조건* 및 명령 플래그를 사용 하 여 개별 UI 요소의 표시 여부를 제어할 수 있습니다.  
  
##### <a name="visibility-constraints"></a>표시 유형 제약 조건  
 표시 제약 조건은 섹션에서 [VisibilityItem 요소로](../../extensibility/visibilityitem-element.md) 설정 됩니다 `VisibilityConstraints` . 표시 제약 조건은 대상 항목이 표시 되는 특정 UI 컨텍스트를 정의 합니다. 이 섹션에 포함 된 메뉴 또는 명령은 정의 된 컨텍스트 중 하나가 활성 상태인 경우에만 표시 됩니다. 이 섹션에서 메뉴 또는 명령이 참조 되지 않는 경우 기본적으로 항상 표시 됩니다. 이 섹션은 그룹에는 적용 되지 않습니다.  
  
 `VisibilityItem` 요소에는 `guid` `id` 대상 UI 요소의 및와 같은 세 가지 특성이 있어야 `context` 합니다. `context`특성은 대상 항목이 표시 되는 시기를 지정 하 고 모든 유효한 UI 컨텍스트를 해당 값으로 사용 합니다. Visual Studio의 UI 컨텍스트 상수는 클래스의 멤버입니다 <xref:Microsoft.VisualStudio.VSConstants> . 모든 `VisibilityItem` 요소에는 하나의 컨텍스트 값만 사용할 수 있습니다. 두 번째 컨텍스트를 적용 하려면 `VisibilityItem` 다음 예제와 같이 동일한 항목을 가리키는 두 번째 요소를 만듭니다.  
  
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
  
##### <a name="command-flags"></a>명령 플래그  
 다음 명령 플래그는 적용 되는 메뉴 및 명령의 표시 여부에 영향을 줄 수 있습니다.  
  
 AlwaysCreate  
 메뉴는 그룹이 나 단추가 없는 경우에도 만들어집니다.  
  
 유효 기간: `Menu`  
  
 CommandWellOnly  
 명령이 최상위 메뉴에 표시 되지 않고 추가 셸 사용자 지정에 사용할 수 있도록 하려면이 플래그를 적용 합니다 (예: 키에 바인딩). VSPackage가 설치 되 면 사용자는 **옵션** 대화 상자를 열고 **키보드 환경** 범주에서 명령 배치를 편집 하 여 이러한 명령을 사용자 지정할 수 있습니다. 바로 가기 메뉴, 도구 모음, 메뉴 컨트롤러 또는 하위 메뉴에 배치 하는 것에는 영향을 주지 않습니다.  
  
 유효 기간: `Button` , `Combo`  
  
 DefaultDisabled  
 명령을 구현 하는 VSPackage이 로드 되지 않았거나 QueryStatus 메서드를 호출 하지 않은 경우에는 기본적으로이 명령을 사용할 수 없습니다.  
  
 유효 기간: `Button` , `Combo`  
  
 DefaultInvisible  
 명령을 구현 하는 VSPackage이 로드 되지 않았거나 QueryStatus 메서드가 호출 되지 않은 경우 기본적으로 명령이 표시 되지 않습니다.  
  
 플래그와 함께 사용 해야 합니다 `DynamicVisibility` .  
  
 유효 기간: `Button` , `Combo` , `Menu`  
  
 DynamicVisibility  
 명령 표시 유형은 QueryStatus 메서드 또는 섹션에 포함 된 컨텍스트 GUID를 사용 하 여 변경할 수 있습니다 `VisibilityConstraints` .  
  
 도구 모음이 아닌 메뉴에 나타나는 명령에 적용 됩니다. OLECMDF_INVISIBLE 플래그가 QueryStatus 메서드에서 반환 될 때 최상위 도구 모음 항목은 사용 하지 않도록 설정할 수 있지만 숨길 수는 없습니다.  
  
 메뉴에서이 플래그는 해당 멤버가 숨겨진 경우에도 자동으로 숨겨지도록 함을 나타냅니다. 최상위 메뉴에는이 동작이 이미 있으므로이 플래그는 일반적으로 하위 메뉴에 할당 됩니다.  
  
 플래그와 함께 사용 해야 합니다 `DefaultInvisible` .  
  
 유효 기간: `Button` , `Combo` , `Menu`  
  
 NoShowOnMenuController  
 이 플래그가 있는 명령이 메뉴 컨트롤러에 배치 되는 경우이 명령은 드롭다운 목록에 표시 되지 않습니다.  
  
 유효 기간: `Button`  
  
 명령 플래그에 대 한 자세한 내용은 [명령 플래그 요소](../../extensibility/command-flag-element.md) 설명서를 참조 하세요.  
  
##### <a name="general-requirements"></a>일반 요구 사항  
 명령을 표시 하 고 사용 하려면 다음 일련의 테스트를 통과 해야 합니다.  
  
- 명령이 올바르게 배치 되었습니다.  
  
- `DefaultInvisible`플래그가 설정 되지 않았습니다.  
  
- 부모 메뉴 또는 도구 모음이 표시 됩니다.  
  
- [VisibilityConstraints 요소](../../extensibility/visibilityconstraints-element.md) 섹션의 컨텍스트 항목 때문에 명령이 표시 되지 않습니다.  
  
- 인터페이스를 구현 하는 VSPackage 코드를 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 표시 하 고 명령을 활성화 합니다. 인터페이스 코드를 가로채이를 처리 합니다.  
  
- 사용자가 명령을 클릭 하면 [라우팅 알고리즘](../../extensibility/internals/command-routing-algorithm.md)에 설명 된 절차가 적용 됩니다.  
  
## <a name="calling-pre-defined-commands"></a>미리 정의 된 명령 호출  
 Vspackage는 [UsedCommands 요소](../../extensibility/usedcommands-element.md) 를 사용 하 여 다른 VSPACKAGE 또는 IDE에서 제공 하는 명령에 액세스할 수 있습니다. 이렇게 하려면 사용할 명령의 GUID 및 ID를 포함 하는 [UsedCommand 요소](../../extensibility/usedcommand-element.md) 를 만듭니다. 이렇게 하면 현재 Visual Studio 구성에 포함 되지 않은 경우에도 명령이 Visual Studio에 로드 됩니다. 자세한 내용은 [UsedCommand 요소](../../extensibility/usedcommand-element.md)를 참조 하세요.  
  
## <a name="interface-element-appearance"></a>인터페이스 요소 모양  
 명령 요소를 선택 하 고 위치를 지정 하기 위한 고려 사항은 다음과 같습니다.  
  
- [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 는 배치에 따라 다르게 표시 되는 다양 한 UI 요소를 제공 합니다.  
  
- 플래그를 사용 하 여 정의 된 UI 요소는 `DefaultInvisible` 메서드의 VSPackage 구현에서 표시 <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> 되거나 섹션의 특정 ui 컨텍스트와 연결 되어 있지 않으면 IDE에 표시 되지 않습니다 `VisibilityConstraints` .  
  
- 성공적으로 배치 된 명령도 표시 되지 않을 수 있습니다. 이는 VSPackage가 구현 하거나 구현 하지 않은 인터페이스에 따라 IDE에서 일부 명령을 자동으로 숨기 거 나 표시 하기 때문입니다. 예를 들어, 일부 빌드 인터페이스의 VSPackage 구현은 빌드 관련 메뉴 항목이 자동으로 표시 되도록 합니다.  
  
- `CommandWellOnly`UI 요소의 정의에 플래그를 적용 하면 사용자 지정을 통해서만 명령을 추가할 수 있습니다.  
  
- 명령은 특정 UI 컨텍스트에서만 사용할 수 있습니다. 예를 들어 IDE가 디자인 뷰에 있을 때 대화 상자가 표시 되는 경우에만 사용할 수 있습니다.  
  
- 특정 UI 요소가 IDE에 표시 되도록 하려면 하나 이상의 인터페이스를 구현 하거나 일부 코드를 작성 해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [메뉴 및 명령 확장](../../extensibility/extending-menus-and-commands.md)

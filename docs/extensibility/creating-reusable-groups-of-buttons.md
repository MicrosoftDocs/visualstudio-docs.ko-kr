---
title: 다시 사용할 수 있는 단추 그룹 만들기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 477014ed77b60821ad191ba6842999be6f528fee
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903644"
---
# <a name="create-reusable-groups-of-buttons"></a>다시 사용할 수 있는 단추 그룹 만들기
명령 그룹은 메뉴 또는 도구 모음에서 항상 함께 표시 되는 명령 모음입니다. 모든 명령 그룹은 *vsct* 파일의 commandplacements 섹션에서 다른 부모 메뉴에 할당 하 여 다시 사용할 수 있습니다.

 명령 그룹에는 일반적으로 단추가 포함 되지만 다른 메뉴 또는 콤보 상자도 포함 될 수 있습니다.

## <a name="to-create-a-reusable-group-of-buttons"></a>다시 사용할 수 있는 단추 그룹을 만들려면

1. 이라는 VSIX 프로젝트를 만듭니다 `ReusableButtons` . 자세한 내용은 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)를 참조 하세요.

2. 프로젝트가 열리면 **ReusableCommand**이라는 사용자 지정 명령 항목 템플릿을 추가 합니다. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **Add**  >  **새 항목**추가를 선택 합니다. **새 항목 추가** 대화 상자에서 **Visual c #**  >  **확장성** 으로 이동 하 고 **사용자 지정 명령**을 선택 합니다. 창 맨 아래에 있는 **이름** 필드에서 명령 파일 이름을 *ReusableCommand.cs*로 변경 합니다.

3. *. Vsct* 파일에서 기호 섹션으로 이동 하 고 프로젝트에 대 한 그룹 및 명령을 포함 하는 GuidSymbol 요소를 찾습니다. 이름을 guidReusableCommandPackageCmdSet로 지정 해야 합니다.

4. 다음 예제와 같이 그룹에 추가할 각 단추에 대해 IDSymbol을 추가 합니다.

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     기본적으로 명령 항목 템플릿은 **Mymenugroup** 이라는 그룹과 사용자가 입력 한 이름을 포함 하는 단추를 각각에 대 한 idsymbol 항목과 함께 만듭니다.

5. 그룹 섹션에서 기호 섹션에 지정 된 것과 동일한 GUID 및 ID 특성을 가진 Group 요소를 만듭니다. 기존 그룹을 사용 하거나 다음 예제와 같이 명령 템플릿에서 제공 하는 항목을 사용할 수도 있습니다. 이 그룹은 **도구** 메뉴에 표시 됩니다.

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>다시 사용할 단추 그룹을 만들려면

1. 명령 또는 메뉴의 정의에서 그룹을 부모로 사용 하거나 CommandPlacements 섹션을 사용 하 여 그룹에 명령 또는 메뉴를 배치 하 여 그룹에 명령 또는 메뉴를 넣을 수 있습니다.

     단추 섹션에서 그룹을 부모로 사용 하는 단추를 정의 하거나 다음 예제와 같이 패키지 템플릿에서 제공 하는 단추를 사용 합니다.

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. 두 개 이상의 그룹에 단추가 표시 되어야 하는 경우 명령 섹션 뒤에 배치 해야 하는 CommandPlacements 섹션에서 해당 항목을 만듭니다. 다음 예제에 표시 된 것과 같이 위치를 지정할 단추의 GUID 및 ID 특성을 일치 하도록 설정 하 고 부모 요소의 GUID 및 id를 대상 그룹의 GUID 및 ID로 설정 합니다.

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    > 우선 순위 필드의 값은 새 명령 그룹에서 명령의 위치를 결정 합니다. CommandPlacement 요소에 설정 된 우선 순위는 항목 정의에 설정 된 우선 순위를 재정의 합니다. 우선 순위 값이 낮은 명령은 우선 순위 값이 높은 명령 앞에 표시 됩니다. 중복 우선 순위 값이 허용 되지만, 우선 순위 값이 동일한 명령의 상대 위치는 **devenv/setup** 명령이 레지스트리에서 최종 인터페이스를 만드는 순서가 일치 하지 않을 수 있기 때문에 보장 될 수 없습니다.

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>메뉴에 다시 사용할 수 있는 단추 그룹을 추가 하려면

1. 섹션에서 항목을 만듭니다 `CommandPlacements` . 요소의 GUID 및 ID를 그룹의 GUID 및 ID로 설정 하 `CommandPlacement` 고 부모 guid 및 id를 대상 위치의 guid로 설정 합니다.

    CommandPlacements 섹션은 명령 섹션 바로 뒤에 배치 해야 합니다.

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    명령 그룹은 둘 이상의 메뉴에 포함 될 수 있습니다. 부모 메뉴는 만든 항목 중 하나 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ( *shellcmddef. vsct* 또는 *sharedcmdvsct*에 설명 된 대로) 또는 다른 VSPackage에서 정의 된 메뉴 중 하나를 사용할 수 있습니다. 부모 메뉴가 결국 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage에 의해 표시 되는 바로 가기 메뉴 또는에 연결 되는 경우에는 부모 메뉴의 수에 제한이 없습니다.

    다음 예에서는 **솔루션 탐색기** 도구 모음에서 다른 단추 오른쪽에 그룹을 배치 합니다.

   ```xml
   <CommandPlacements>
       <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00">
         <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
       </CommandPlacement>
   </CommandPlacements>
   ```

   ```xml
   <CommandPlacements>
     <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup"
         priority="0x605">
       <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" />
     </CommandPlacement>
   </CommandPlacements>

   ```

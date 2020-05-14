---
title: 재사용 가능한 단추 그룹 만들기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: ddfba6701890f73ce6438ddc03a338912841a37d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739470"
---
# <a name="create-reusable-groups-of-buttons"></a>재사용 가능한 단추 그룹 만들기
명령 그룹은 메뉴 또는 도구 모음에 항상 함께 표시되는 명령 모음입니다. *.vsct* 파일의 CommandPlacements 섹션의 다른 상위 메뉴에 할당하여 모든 명령 그룹을 다시 사용할 수 있습니다.

 명령 그룹에는 일반적으로 단추가 포함되지만 다른 메뉴 나 콤보 상자를 포함할 수도 있습니다.

## <a name="to-create-a-reusable-group-of-buttons"></a>재사용 가능한 단추 그룹을 만들려면

1. 라는 VSIX 프로젝트를 `ReusableButtons`만듭니다. 자세한 내용은 [메뉴 명령을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-menu-command.md)참조하십시오.

2. 프로젝트가 열리면 **재사용 가능한 명령이라는**사용자 지정 명령 항목 템플릿을 추가합니다. 솔루션 **탐색기에서**프로젝트 노드를 마우스 오른쪽 단추로 클릭하고**새 항목** **추가를** > 선택합니다. 새 **항목 추가** 대화 상자에서 **시각적 C#** > **확장성으로** 이동하여 **사용자 지정 명령을 선택합니다.** 창 아래쪽의 **이름** 필드에서 명령 파일 이름을 *ReusableCommand.cs.*

3. *.vsct* 파일에서 기호 섹션으로 이동하여 프로젝트에 대한 그룹 및 명령이 포함된 GuidSymbol 요소를 찾습니다. 그것은 guid의 이름을 지정해야합니다재사용 가능한명령패키지CmdSet.

4. 다음 예제와 같이 그룹에 추가할 각 단추에 대한 IDSymbol를 추가합니다.

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     기본적으로 명령 항목 템플릿은 **MyMenuGroup이라는** 그룹과 제공한 이름이 있는 단추와 각각에 대한 IDSymbol 항목을 만듭니다.

5. 그룹 섹션에서 기호 섹션에 지정된 것과 동일한 GUID 및 ID 특성을 가지는 그룹 요소를 만듭니다. 다음 예제와 같이 기존 그룹을 사용하거나 명령 템플릿에서 제공하는 항목을 사용할 수도 있습니다. 이 그룹은 **도구** 메뉴에 나타납니다.

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>재사용할 단추 그룹을 만들려면

1. 명령 또는 메뉴의 정의에서 그룹을 부모로 사용하거나 CommandPlacements 섹션을 사용하여 그룹에 명령 또는 메뉴를 배치하여 그룹에 명령 또는 메뉴를 배치할 수 있습니다.

     단추 섹션에서는 다음 예제와 같이 그룹이 상위로 있는 단추를 정의하거나 패키지 템플릿에서 제공하는 단추를 사용합니다.

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. 단추가 두 개 이상의 그룹에 나타나야 하는 경우 명령 위치 섹션에서 단추에 대한 항목을 만드며, 이 항목은 명령 섹션 다음위치에 배치되어야 합니다. CommandPlacement 요소의 GUID 및 ID 속성을 배치하려는 단추의 속성과 일치하도록 설정한 다음 다음 예제와 같이 해당 상위 요소의 GUID 및 ID를 대상 그룹의 GUID 및 ID로 설정합니다.

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    > Priority 필드의 값은 새 명령 그룹의 명령 위치를 결정합니다. CommandPlacement 요소에 설정된 우선 순위는 항목 정의에서 해당 집합을 재정의합니다. 우선 순위가 낮은 값이 있는 명령은 우선 순위 값이 높은 명령 앞에 표시됩니다. 중복 우선 순위 값은 허용되지만 **devenv /setup** 명령이 레지스트리에서 최종 인터페이스를 만드는 순서가 일치하지 않을 수 있으므로 우선 순위 값이 같은 명령의 상대적 위치를 보장할 수 없습니다.

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>메뉴에 재사용 가능한 단추 그룹을 넣습니다.

1. `CommandPlacements` 섹션에서 항목을 만듭니다. 요소의 GUID 및 `CommandPlacement` ID를 그룹의 GUID 및 ID로 설정하고 상위 GUID 및 ID를 대상 위치의 GUID 및 ID로 설정합니다.

    명령 위치 섹션은 명령 섹션 바로 바로 위에 배치해야 합니다.

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    명령 그룹은 두 개 이상의 메뉴에 포함될 수 있습니다. 상위 메뉴는 생성한 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 메뉴이거나, 제공된 메뉴(ShellCmdDef.vsct 또는 *SharedCmdDef.vsct)에*설명된 메뉴이거나 다른 VSPackage에 정의된 메뉴일 수 있습니다. *ShellCmdDef.vsct* 상위 메뉴가 결국 VSPackage에 의해 표시되는 바로 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 가기 메뉴에 연결되는 한 상위 레이어의 수는 무제한입니다.

    다음 예제에서는 그룹을 **솔루션 탐색기** 도구 모음에 다른 단추의 오른쪽에 놓습니다.

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

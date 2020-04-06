---
title: 도구 모음 추가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 655cd87fe59cf4f42361cc24a63eb56653caae1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740225"
---
# <a name="add-a-toolbar"></a>도구 모음 추가
이 연습에서는 Visual Studio IDE에 도구 모음을 추가하는 방법을 보여 주며, 도구 모음을 추가합니다.

 도구 모음은 명령에 바인딩된 단추를 포함하는 가로 또는 세로 스트립입니다. 구현에 따라 IDE의 도구 모음을 재배치하거나, 기본 IDE 창의 어느 쪽에도 도킹하거나, 다른 창 앞에 머물 수 있습니다.

 또한 사용자는 **사용자 지정** 대화 상자를 사용하여 도구 모음에 명령을 추가하거나 명령을 제거할 수 있습니다. 일반적으로 VSPackage의 도구 모음은 사용자 지정이 가능합니다. IDE는 모든 사용자 지정을 처리하고 VSPackage는 명령에 응답합니다. VSPackage는 명령이 물리적으로 있는 위치를 알 필요가 없습니다.

 메뉴에 대한 자세한 내용은 [명령, 메뉴 및 도구 모음을](../extensibility/internals/commands-menus-and-toolbars.md)참조하십시오.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. 시각적 스튜디오 설정에서 선택적 기능으로 포함됩니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-an-extension-with-a-toolbar"></a>도구 모음으로 확장 만들기
 라는 VSIX 프로젝트를 `IDEToolbar`만듭니다. **ToolbarTestCommand이라는**메뉴 명령 항목 템플릿을 추가합니다. 이 작업을 수행하는 방법에 대한 자세한 내용은 [메뉴 명령을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-menu-command.md)참조하십시오.

## <a name="create-a-toolbar-for-the-ide"></a>IDE에 대한 도구 모음 만들기

1. *도구 모음TestCommandPackage.vsct에서*기호 섹션을 찾습니다. guidToolBarTestCommandPackageCmdSet이라는 GuidSymbol 요소에서 다음과 같이 도구 모음 및 도구 모음 그룹에 대한 선언을 추가합니다.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. 명령 섹션 의 맨 위에 메뉴 섹션을 만듭니다. 메뉴 섹션에 메뉴 요소를 추가하여 도구 모음을 정의합니다.

    ```xml
    <Menus>
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"
            type="Toolbar" >
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
          </Menu>
    </Menus>
    ```

     도구 모음은 하위 메뉴처럼 중첩될 수 없습니다. 따라서 부모 그룹을 할당할 필요가 없습니다. 또한 사용자가 도구 모음을 이동할 수 있으므로 우선 순위를 설정할 필요가 없습니다. 일반적으로 도구 모음의 초기 배치는 프로그래밍 방식으로 정의되지만 사용자에 의한 후속 변경은 유지됩니다.

3. [그룹](../extensibility/groups-element.md) 섹션에서 기존 그룹 항목 후 도구 모음에 대한 명령을 포함하도록 [그룹](../extensibility/group-element.md) 요소를 정의합니다.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. 도구 모음에 단추가 나타나도록 합니다. 단추 섹션에서 단추의 상위 블록을 도구 모음으로 바꿉습니다. 결과 단추 블록은 다음과 같아야 합니다.

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     기본적으로 도구 모음에 명령이 없는 경우 나타나지 않습니다.

5. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타나야 합니다.

6. [Visual Studio] 메뉴 모음을 마우스 오른쪽 버튼으로 클릭하여 도구 모음 목록을 가져옵니다. **테스트 도구 모음을**선택합니다.

7. 이제 도구 모음이 파일에서 찾기 아이콘 오른쪽에 있는 아이콘으로 표시됩니다. 아이콘을 클릭하면 **ToolbarTestCommandPackage라는 메시지 상자가 표시됩니다. 내부 IDEToolbar.ToolbarTestCommand.MenuItemCallback()**.

## <a name="see-also"></a>참조
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)

---
title: 도구 모음 추가 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: beb97356daf3c932470bf2598e58e1f5b40ea233
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904077"
---
# <a name="add-a-toolbar"></a>도구 모음 추가
이 연습에서는 Visual Studio IDE에 도구 모음을 추가 하는 방법을 보여 줍니다.

 도구 모음은 명령에 바인딩되는 단추를 포함 하는 가로 또는 세로 줄무늬입니다. 구현에 따라 IDE의 도구 모음을 위치 변경 하거나 주 IDE 창의 어느 쪽에 나 도킹 하거나 다른 창 앞에 유지 하도록 만들 수 있습니다.

 또한 사용자는 사용자 **지정** 대화 상자를 사용 하 여 도구 모음에 명령을 추가 하거나 제거할 수 있습니다. 일반적으로 Vspackage의 도구 모음은 사용자가 사용자 지정할 수 있습니다. IDE는 모든 사용자 지정을 처리 하 고 VSPackage는 명령에 응답 합니다. VSPackage는 명령이 실제로 위치한 위치를 알 필요가 없습니다.

 메뉴에 대 한 자세한 내용은 [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)을 참조 하세요.

## <a name="prerequisites"></a>필수 구성 요소
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="create-an-extension-with-a-toolbar"></a>도구 모음을 사용 하 여 확장 만들기
 이라는 VSIX 프로젝트를 만듭니다 `IDEToolbar` . **ToolbarTestCommand**라는 메뉴 명령 항목 템플릿을 추가 합니다. 이 작업을 수행 하는 방법에 대 한 자세한 내용은 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)를 참조 하세요.

## <a name="create-a-toolbar-for-the-ide"></a>IDE에 대 한 도구 모음 만들기

1. *ToolbarTestCommandPackage*에서 기호 섹션을 찾습니다. GuidToolbarTestCommandPackageCmdSet 라는 GuidSymbol 요소에서 다음과 같이 도구 모음 및 도구 모음 그룹에 대 한 선언을 추가 합니다.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. 명령 섹션의 맨 위에서 메뉴 섹션을 만듭니다. 메뉴 섹션에 메뉴 요소를 추가 하 여 도구 모음을 정의 합니다.

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

     도구 모음은 하위 메뉴와 같이 중첩 될 수 없습니다. 따라서 부모 그룹을 할당할 필요가 없습니다. 또한 사용자가 도구 모음을 이동할 수 있으므로 우선 순위를 설정할 필요가 없습니다. 일반적으로 도구 모음의 초기 배치는 프로그래밍 방식으로 정의 되지만 사용자의 후속 변경 내용은 유지 됩니다.

3. [그룹](../extensibility/groups-element.md) 섹션에서 기존 그룹 항목 뒤에 도구 모음에 대 한 명령을 포함 하는 [group](../extensibility/group-element.md) 요소를 정의 합니다.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. 도구 모음에 단추가 표시 되도록 합니다. 단추 섹션에서 단추의 부모 블록을 도구 모음으로 바꿉니다. 결과 단추 블록은 다음과 같습니다.

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     기본적으로 도구 모음에 명령이 없으면 표시 되지 않습니다.

5. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 표시 되어야 합니다.

6. Visual Studio 메뉴 모음을 마우스 오른쪽 단추로 클릭 하 여 도구 모음 목록을 가져옵니다. **테스트 도구 모음**을 선택 합니다.

7. 이제 도구 모음이 파일에서 찾기 아이콘의 오른쪽에 아이콘으로 표시 됩니다. 아이콘을 클릭 하면 ToolbarTestCommandPackage 라는 메시지 상자가 표시 됩니다 **. ToolbarTestCommand. MenuItemCallback () 내부 IDEToolbar**.

## <a name="see-also"></a>추가 정보
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)

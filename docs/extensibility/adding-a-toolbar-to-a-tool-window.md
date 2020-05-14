---
title: 도구 창에 도구 모음 추가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 094515eb94279623974bd7b55cc9923c49625a70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740250"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>도구 창에 도구 모음 추가
이 연습에서는 도구 모음을 도구 창에 추가하는 방법을 보여 주며, 도구 모음을 추가합니다.

 도구 모음은 명령에 바인딩된 단추가 포함된 가로 또는 세로 스트립입니다. 도구 창의 도구 모음 길이는 도구 모음이 도킹된 위치에 따라 공구 창의 너비 나 높이와 항상 동일합니다.

 IDE의 도구 모음과 달리 도구 창의 도구 모음은 도킹되어야 하며 이동하거나 사용자 지정할 수 없습니다. VSPackageumanaged 코드로 작성 된 경우 도구 모음은 모든 가장자리에 도킹 될 수 있습니다.

 도구 모음을 추가하는 방법에 대한 자세한 내용은 [도구 모음 추가 를](../extensibility/adding-a-toolbar.md)참조하십시오.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. 시각적 스튜디오 설정에서 선택적 기능으로 포함됩니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-a-toolbar-for-a-tool-window"></a>도구 창에 대한 도구 모음 만들기

1. **TWTestCommand이라는** `TWToolbar` 메뉴 명령과 **TestToolWindow라는**도구 창이 모두 있는 VSIX 프로젝트를 만듭니다. 자세한 내용은 [메뉴 명령을 사용하여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md) 및 도구 창을 사용하여 확장 [만들기를](../extensibility/creating-an-extension-with-a-tool-window.md)참조하십시오. 도구 창 템플릿을 추가하기 전에 명령 항목 템플릿을 추가해야 합니다.

2. *TWTestCommandPackage.vsct에서*기호 섹션을 찾습니다. guidTWTestCommandPackageCmdSet이라는 GuidSymbol 노드에서 다음과 같이 도구 모음 및 도구 모음 그룹을 선언합니다.

    ```xml
    <IDSymbol name="TWToolbar" value="0x1000" />
    <IDSymbol name="TWToolbarGroup" value="0x1050" />
    ```

3. `Commands` 단면 의 맨 위에 `Menus` 단면을 작성합니다. `Menu` 요소를 추가하여 도구 모음을 정의합니다.

    ```xml
    <Menus>
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

     도구 모음은 하위 메뉴처럼 중첩될 수 없습니다. 따라서 부모를 할당할 필요가 없습니다. 또한 사용자가 도구 모음을 이동할 수 있으므로 우선 순위를 설정할 필요가 없습니다. 일반적으로 도구 모음의 초기 배치는 프로그래밍 방식으로 정의되지만 사용자에 의한 후속 변경은 유지됩니다.

4. 그룹 섹션에서 도구 모음에 대한 명령을 포함하도록 그룹을 정의합니다.

    ```xml

    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />
    </Group>
    ```

5. 단추 섹션에서 도구 모음이 표시되도록 기존 Button 요소의 상위를 도구 모음 그룹으로 변경합니다.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke TWTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     기본적으로 도구 모음에 명령이 없는 경우 나타나지 않습니다.

     새 도구 모음이 도구 창에 자동으로 추가되지 않으므로 도구 모음을 명시적으로 추가해야 합니다. 이에 대해서는 다음 섹션에서 설명합니다.

## <a name="add-the-toolbar-to-the-tool-window"></a>도구 모음을 도구 창에 추가

1. *TWTestCommandPackageGuids.cs* 다음 줄을 추가합니다.

    ```csharp
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const int TWToolbar = 0x1000;
    ```

2. *TestToolWindow.cs* 다음 을 추가 하십시오 using 문.

    ```csharp
    using System.ComponentModel.Design;
    ```

3. TestToolWindow 생성자에서 다음 줄을 추가합니다.

    ```csharp
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);
    ```

## <a name="test-the-toolbar-in-the-tool-window"></a>도구 창에서 도구 모음 테스트

1. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio 실험 인스턴스가 나타납니다.

2. 보기 **/ 기타 Windows** 메뉴에서 **테스트 도구창을** 클릭하여 도구 창을 표시합니다.

     도구 창의 왼쪽 상단에 제목 바로 아래에 도구 모음(기본 아이콘처럼 보아도)이 표시됩니다.

3. 도구 모음에서 아이콘을 클릭하여 **TWToolbar.TWTestCommand.MenuItemCallback() 내부에 TWTestCommandPackage 메시지를**표시합니다.

## <a name="see-also"></a>참조
- [도구 모음 추가](../extensibility/adding-a-toolbar.md)

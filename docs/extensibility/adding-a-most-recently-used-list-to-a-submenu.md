---
title: 하위 메뉴에 가장 최근에 사용한 목록 추가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf389c0da7ec0aafb6e47dae8f09ffdc3b1d1e4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740294"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>하위 메뉴에 가장 최근에 사용한 목록 추가
이 연습에서는 [메뉴에 하위 메뉴 추가의](../extensibility/adding-a-submenu-to-a-menu.md)데모를 빌드하고 하위 메뉴에 동적 목록을 추가하는 방법을 보여 줍니다. 동적 목록은 가장 최근에 사용한(MRU) 목록을 만들기 위한 기초를 형성합니다.

동적 메뉴 목록은 메뉴의 자리 표시자로 시작합니다. 메뉴가 표시될 때마다 Visual Studio 통합 개발 환경(IDE)은 자리 표시자에서 표시해야 하는 모든 명령에 대해 VSPackage에 요청합니다. 동적 목록은 메뉴의 아무 곳에서나 발생할 수 있습니다. 그러나 동적 목록은 일반적으로 하위 메뉴 또는 메뉴 하단에 저장되고 표시됩니다. 이러한 디자인 패턴을 사용하면 메뉴의 다른 명령 위치에 영향을 주지 않고 동적 명령 목록을 확장하고 축소할 수 있습니다. 이 연습에서는 동적 MRU 목록이 기존 하위 메뉴의 맨 아래에 표시되고 나머지 하위 메뉴와 줄로 구분됩니다.

기술적으로 동적 목록을 도구 모음에 적용할 수도 있습니다. 그러나 사용자가 변경하기 위한 특정 단계를 취하지 않는 한 도구 모음은 변경되지 않아야 하므로 이러한 사용은 권장되지 않습니다.

이 연습에서는 그 중 하나가 선택될 때마다 순서를 변경하는 네 개의 항목으로 구성된 MRU 목록을 만듭니다(선택한 항목이 목록의 맨 위로 이동).

메뉴 및 *.vsct* 파일에 대한 자세한 내용은 [명령, 메뉴 및 도구 모음을](../extensibility/internals/commands-menus-and-toolbars.md)참조하십시오.

## <a name="prerequisites"></a>사전 요구 사항
이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)를 참조하십시오.

## <a name="create-an-extension"></a>확장 만들기

- [메뉴에 하위 메뉴 추가의](../extensibility/adding-a-submenu-to-a-menu.md) 절차를 수행하여 다음 절차에서 수정된 하위 메뉴를 만듭니다.

  이 연습의 절차는 VSPackage의 `TopLevelMenu`이름이 Visual Studio 메뉴 [모음에 메뉴 추가에](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)사용되는 이름인 것으로 가정합니다.

## <a name="create-a-dynamic-item-list-command"></a>동적 항목 목록 명령 만들기

1. *오픈 테스트명령 패키지.vsct*.

2. 섹션에서 `Symbols` guidTestCommandPackageCmdSet이라는 `GuidSymbol` 노드에서 `MRUListGroup` 다음과 같이 그룹 및 명령에 `cmdidMRUList` 대한 기호를 추가합니다.

    ```csharp
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. 섹션에서 `Groups` 기존 그룹 항목 다음의 선언된 그룹을 추가합니다.

    ```cpp
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>

    ```

4. 섹션에서 `Buttons` 기존 단추 항목 다음에서 새로 선언된 명령을 나타내는 노드를 추가합니다.

    ```csharp
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidMRUList"
        type="Button" priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="MRUListGroup" />
        <CommandFlag>DynamicItemStart</CommandFlag>
        <Strings>
            <CommandName>cmdidMRUList</CommandName>
            <ButtonText>MRU Placeholder</ButtonText>
        </Strings>
    </Button>
    ```

    플래그를 `DynamicItemStart` 사용하면 명령을 동적으로 생성할 수 있습니다.

5. 프로젝트를 빌드하고 디버깅을 시작하여 새 명령의 표시를 테스트합니다.

    **TestMenu** 메뉴에서 새 하위 메뉴인 **하위 메뉴를**클릭하여 새 **명령MRU 자리 표시자를**표시합니다. 다음 절차에서 동적 MRU 명령 목록이 구현되면 하위 메뉴가 열릴 때마다 이 명령 레이블이 해당 목록으로 바뀝습니다.

## <a name="filling-the-mru-list"></a>MRU 목록 채우기

1. *TestCommandPackageGuids.cs* `TestCommandPackageGuids` 클래스 정의에서 기존 명령 아이디 다음에 다음 줄을 추가합니다.

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. *TestCommand.cs* 다음 using 문을 추가합니다.

    ```csharp
    using System.Collections;
    ```

3. 마지막 AddCommand 호출 후 TestCommand 생성자에서 다음 코드를 추가합니다. 는 `InitMRUMenu` 나중에 정의됩니다.

    ```csharp
    this.InitMRUMenu(commandService);
    ```

4. TestCommand 클래스에 다음 코드를 추가합니다. 이 코드는 MRU 목록에 표시할 항목을 나타내는 문자열 목록을 초기화합니다.

    ```csharp
    private int numMRUItems = 4;
    private int baseMRUID = (int)TestCommandPackageGuids.cmdidMRUList;
    private ArrayList mruList;

    private void InitializeMRUList()
    {
        if (null == this.mruList)
        {
            this.mruList = new ArrayList();
            if (null != this.mruList)
            {
                for (int i = 0; i < this.numMRUItems; i++)
                {
                    this.mruList.Add(string.Format(CultureInfo.CurrentCulture,
                        "Item {0}", i + 1));
                }
            }
        }
    }
    ```

5. 메서드 `InitializeMRUList` 후 메서드를 `InitMRUMenu` 추가합니다. 이렇게 하면 MRU 목록 메뉴 명령이 초기화됩니다.

    ```csharp
    private void InitMRUMenu(OleMenuCommandService mcs)
    {
        InitializeMRUList();
        for (int i = 0; i < this.numMRUItems; i++)
        {
            var cmdID = new CommandID(
                new Guid(TestCommandPackageGuids.guidTestCommandPackageCmdSet), this.baseMRUID + i);
            var mc = new OleMenuCommand(
                new EventHandler(OnMRUExec), cmdID);
            mc.BeforeQueryStatus += new EventHandler(OnMRUQueryStatus);
            mcs.AddCommand(mc);
        }
    }
    ```

    MRU 목록에서 가능한 모든 항목에 대해 메뉴 명령 개체를 만들어야 합니다. IDE는 더 `OnMRUQueryStatus` 이상 항목이 없을 때까지 MRU 목록의 각 항목에 대한 메서드를 호출합니다. 관리 코드에서 IDE가 더 이상 항목이 없다는 것을 알 수 있는 유일한 방법은 가능한 모든 항목을 먼저 만드는 것입니다. 원하는 경우 메뉴 명령을 만든 후 사용하여 `mc.Visible = false;` 추가 항목을 처음에는 표시되지 않는 것으로 표시할 수 있습니다. 그런 다음 `mc.Visible = true;` `OnMRUQueryStatus` 이러한 항목은 나중에 메서드에서 사용하여 표시할 수 있습니다.

6. 메서드 `InitMRUMenu` 후 다음 `OnMRUQueryStatus` 메서드를 추가합니다. 각 MRU 항목에 대한 텍스트를 설정하는 처리기입니다.

    ```csharp
    private void OnMRUQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                menuCommand.Text = this.mruList[MRUItemIndex] as string;
            }
        }
    }
    ```

7. 메서드 `OnMRUQueryStatus` 후 다음 `OnMRUExec` 메서드를 추가합니다. MRU 항목을 선택하기 위한 처리기입니다. 이 메서드는 선택한 항목을 목록의 맨 위로 이동한 다음 선택한 항목을 메시지 상자에 표시합니다.

    ```csharp
    private void OnMRUExec(object sender, EventArgs e)
    {
        var menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                string selection = this.mruList[MRUItemIndex] as string;
                for (int i = MRUItemIndex; i > 0; i--)
                {
                    this.mruList[i] = this.mruList[i - 1];
                }
                this.mruList[0] = selection;
                System.Windows.Forms.MessageBox.Show(
                    string.Format(CultureInfo.CurrentCulture,
                                  "Selected {0}", selection));
            }
        }
    }

    ```

## <a name="testing-the-mru-list"></a>MRU 목록 테스트

1. 프로젝트를 빌드하고 디버깅을 시작합니다.

2. 테스트 **메뉴** 메뉴에서 **테스트 명령 호출을**클릭합니다. 이렇게 하면 명령이 선택되었다는 메시지 상자가 표시됩니다.

    > [!NOTE]
    > 이 단계는 VSPackage가 MRU 목록을 로드하고 올바르게 표시하도록 하는 데 필요합니다. 이 단계를 건너뛰면 MRU 목록이 표시되지 않습니다.

3. 테스트 **메뉴에서** 하위 **메뉴를 클릭합니다.** 구분 기호 아래에 하위 메뉴 의 끝에 네 개의 항목 목록이 표시됩니다. **항목 3을**클릭하면 메시지 상자가 표시되고 텍스트, **선택항목 3을**표시해야 합니다. 네 개의 항목 목록이 표시되지 않으면 이전 단계의 지침을 따랐는지 확인합니다.

4. 하위 메뉴를 다시 엽니다. 항목 **3이** 이제 목록의 맨 위에 있고 다른 항목이 한 위치로 밀려났습니다. **항목 3을** 다시 클릭하고 메시지 상자에 **선택한 항목 3이**여전히 표시되어 텍스트가 명령 레이블과 함께 새 위치로 올바르게 이동되었음을 나타냅니다.

## <a name="see-also"></a>참조
- [메뉴 항목 동적으로 추가](../extensibility/dynamically-adding-menu-items.md)

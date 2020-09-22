---
title: 가장 최근에 사용한 목록을 하위 메뉴에 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
caps.latest.revision: 47
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caccf8923a8614ceedb7198e218ca2bb14bb7ec0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841594"
---
# <a name="adding-a-most-recently-used-list-to-a-submenu"></a>하위 메뉴에 가장 최근에 사용한 메뉴 목록 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습은 [메뉴에 하위](../extensibility/adding-a-submenu-to-a-menu.md)메뉴를 추가 하는 데모를 기반으로 하며, 동적 목록을 하위 메뉴에 추가 하는 방법을 보여 줍니다. 동적 목록은 MRU (가장 최근에 사용 됨) 목록을 만들기 위한 기본을 형성 합니다.  
  
 동적 메뉴 목록은 메뉴의 자리 표시자로 시작 합니다. Visual Studio IDE (통합 개발 환경)는 메뉴가 표시 될 때마다 자리 표시자에 표시 되어야 하는 모든 명령에 대해 VSPackage에 요청 합니다. 동적 목록은 메뉴의 모든 위치에서 발생할 수 있습니다. 그러나 동적 목록은 일반적으로 하위 메뉴 또는 메뉴의 아래쪽에 저장 되 고 표시 됩니다. 이러한 디자인 패턴을 사용 하 여 메뉴의 다른 명령 위치에 영향을 주지 않고 동적 명령 목록을 확장 하 고 계약을 확장할 수 있습니다. 이 연습에서는 동적 MRU 목록이 기존 하위 메뉴의 아래쪽에 표시 되 고 하위 메뉴의 나머지 부분에서 줄로 구분 됩니다.  
  
 기술적으로는 동적 목록을 도구 모음에도 적용할 수 있습니다. 그러나 사용자가 특정 단계를 변경 하는 경우를 제외 하 고 도구 모음이 변경 되지 않은 상태로 유지 되기 때문에 사용 하지 않는 것이 좋습니다.  
  
 이 연습에서는 두 항목 중 하나가 선택 될 때마다 순서를 변경 하는 네 개의 항목 (선택 된 항목이 목록의 맨 위로 이동)의 MRU 목록을 만듭니다.  
  
 메뉴 및 vsct 파일에 대 한 자세한 내용은 [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)을 참조 하세요.  
  
## <a name="prerequisites"></a>전제 조건  
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md)를 참조 하세요.  
  
## <a name="creating-an-extension"></a>확장 만들기  
  
- [메뉴에 하위 메뉴 추가](../extensibility/adding-a-submenu-to-a-menu.md) 의 절차에 따라 다음 절차에서 수정 된 하위 메뉴를 만듭니다.  
  
  이 연습의 절차에서는 VSPackage 이름이 이며 `TopLevelMenu` [Visual Studio 메뉴 모음에 메뉴를 추가](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)하는 데 사용 되는 이름 이라고 가정 합니다.  
  
## <a name="creating-a-dynamic-item-list-command"></a>동적 항목 목록 명령 만들기  
  
1. TestCommandPackage. vsct를 엽니다.  
  
2. 섹션에서 `Symbols` `GuidSymbol` 다음과 같이 guidTestCommandPackageCmdSet 라는 노드의 그룹 및 명령에 대 한 기호를 추가 `MRUListGroup` `cmdidMRUList` 합니다.  
  
    ```csharp  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3. 섹션에서 `Groups` 기존 그룹 항목 뒤에 선언 된 그룹을 추가 합니다.  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4. 섹션에서 `Buttons` 새로 선언 된 명령을 나타내는 노드를 기존 단추 항목 뒤에 추가 합니다.  
  
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
  
     `DynamicItemStart`플래그를 사용 하면 명령을 동적으로 생성할 수 있습니다.  
  
5. 프로젝트를 빌드하고 디버깅을 시작 하 여 새 명령의 표시를 테스트 합니다.  
  
     **Testmenu** 메뉴에서 새 하위 **메뉴, 하위 메뉴**를 클릭 하 여 새 명령 **MRU 자리 표시자**를 표시 합니다. 다음 절차에서 동적 MRU 명령이 구현 된 후이 명령 레이블은 하위 메뉴가 열릴 때마다 해당 목록으로 대체 됩니다.  
  
## <a name="filling-the-mru-list"></a>MRU 목록 채우기  
  
1. TestCommandPackageGuids.cs에서 클래스 정의의 기존 명령 Id 뒤에 다음 줄을 추가 합니다 `TestCommandPackageGuids` .  
  
    ```csharp  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2. TestCommand.cs에서 다음 using 문을 추가 합니다.  
  
    ```csharp  
    using System.Collections;  
    ```  
  
3. TestCommand 생성자에서 마지막 AddCommand 호출 뒤에 다음 코드를 추가 합니다. 는 `InitMRUMenu` 나중에 정의 됩니다.  
  
    ```csharp  
    this.InitMRUMenu(commandService);  
    ```  
  
4. TestCommand 클래스에 다음 코드를 추가 합니다. 이 코드는 MRU 목록에 표시할 항목을 나타내는 문자열 목록을 초기화 합니다.  
  
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
  
5. 메서드 뒤에 `InitializeMRUList` 메서드를 추가 `InitMRUMenu` 합니다. 그러면 MRU 목록 메뉴 명령이 초기화 됩니다.  
  
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
  
     MRU 목록에서 가능한 모든 항목에 대 한 메뉴 명령 개체를 만들어야 합니다. IDE는 `OnMRUQueryStatus` 항목이 더 이상 없을 때까지 MRU 목록의 각 항목에 대해 메서드를 호출 합니다. 관리 코드에서 IDE가 더 이상 항목이 없다는 것을 알 수 있는 유일한 방법은 먼저 모든 항목을 만드는 것입니다. 원하는 경우 `mc.Visible = false;` 메뉴 명령이 만들어진 후를 사용 하 여 추가 항목을 처음에 표시 되지 않는 것으로 표시할 수 있습니다. 이러한 항목은 나중에 메서드에서를 사용 하 여 볼 수 있습니다 `mc.Visible = true;` `OnMRUQueryStatus` .  
  
6. 메서드 뒤에 `InitMRUMenu` 다음 메서드를 추가 `OnMRUQueryStatus` 합니다. 각 MRU 항목에 대 한 텍스트를 설정 하는 처리기입니다.  
  
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
  
7. 메서드 뒤에 `OnMRUQueryStatus` 다음 메서드를 추가 `OnMRUExec` 합니다. MRU 항목을 선택 하기 위한 처리기입니다. 이 메서드는 선택한 항목을 목록 맨 위로 이동한 다음 선택한 항목을 메시지 상자에 표시 합니다.  
  
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
  
#### <a name="to-test-the-mru-menu-list"></a>MRU 메뉴 목록을 테스트 하려면  
  
1. 프로젝트를 빌드하고 디버깅을 시작 합니다.  
  
2. **Testmenu** 메뉴에서 **testmenu 호출**을 클릭 합니다. 이렇게 하면 명령이 선택 되었음을 나타내는 메시지 상자가 표시 됩니다.  
  
    > [!NOTE]
    > 이 단계는 VSPackage을 강제로 로드 하 고 MRU 목록을 올바르게 표시 하는 데 필요 합니다. 이 단계를 건너뛰면 MRU 목록이 표시 되지 않습니다.  
  
3. **테스트 메뉴** 메뉴에서 **하위 메뉴**를 클릭 합니다. 하위 메뉴의 끝에 표시 되는 네 개의 항목 목록이 구분 기호 아래에 표시 됩니다. **항목 3**을 클릭 하면 메시지 상자가 표시 되 고 "선택한 항목 3" 텍스트를 표시 합니다. (4 개 항목 목록이 표시 되지 않는 경우 이전 단계의 지침을 따랐는지 확인 합니다.)  
  
4. 하위 메뉴를 다시 엽니다. 이제 **항목 3** 이 목록의 맨 위에 있고 다른 항목은 한 위치 아래로 푸시 되었습니다. **항목 3** 을 다시 클릭 하면 메시지 상자에 "선택한 항목 3"이 표시 됩니다 .이는 텍스트를 명령 레이블과 함께 새 위치로 올바르게 이동 했음을 나타냅니다.  
  
## <a name="see-also"></a>참고 항목  
 [메뉴 항목 동적 추가](../extensibility/dynamically-adding-menu-items.md)

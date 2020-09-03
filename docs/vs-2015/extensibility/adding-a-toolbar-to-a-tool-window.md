---
title: 도구 창에 도구 모음 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
caps.latest.revision: 49
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2c5df1ce1721c63b5c5cfc3c5b94929da088660f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184874"
---
# <a name="adding-a-toolbar-to-a-tool-window"></a>도구 창에 도구 모음 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 도구 창에 도구 모음을 추가 하는 방법을 보여 줍니다.  
  
 도구 모음은 명령에 바인딩된 단추를 포함 하는 가로 또는 세로 줄무늬입니다. 도구 창에서 도구 모음의 길이는 도구 모음의 도킹 위치에 따라 항상 도구 창의 너비 또는 높이와 동일 합니다.  
  
 IDE의 도구 모음과 달리 도구 창의 도구 모음은 도킹 되어야 하며 이동 하거나 사용자 지정할 수 없습니다. VSPackage가 umanaged 된 코드로 작성 된 경우 도구 모음을 가장자리에 도킹할 수 있습니다.  
  
 도구 모음을 추가 하는 방법에 대 한 자세한 내용은 [도구 모음 추가](../extensibility/adding-a-toolbar.md)를 참조 하세요.  
  
## <a name="prerequisites"></a>사전 준비 사항  
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.  
  
## <a name="creating-a-toolbar-for-a-tool-window"></a>도구 창에 대 한 도구 모음 만들기  
  
1. `TWToolbar` **Twtestcommand** 라는 메뉴 명령과 **TestToolWindow**라는 도구 창을 모두 포함 하는 라는 VSIX 프로젝트를 만듭니다. 자세한 내용은 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md) 및 [도구 창을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-tool-window.md)를 참조 하세요. 도구 창 템플릿을 추가 하기 전에 명령 항목 템플릿을 추가 해야 합니다.  
  
2. TWTestCommandPackage. vsct에서 기호 섹션을 찾습니다. GuidTWTestCommandPackageCmdSet 라는 GuidSymbol 노드에서 다음과 같이 도구 모음과 도구 모음 그룹을 선언 합니다.  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3. 섹션 위쪽에서 섹션을 `Commands` 만듭니다 `Menus` . 요소를 추가 `Menu` 하 여 도구 모음을 정의 합니다.  
  
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
  
     도구 모음은 하위 메뉴와 같이 중첩 될 수 없습니다. 따라서 부모를 할당할 필요가 없습니다. 또한 사용자가 도구 모음을 이동할 수 있으므로 우선 순위를 설정할 필요가 없습니다. 일반적으로 도구 모음의 초기 배치는 프로그래밍 방식으로 정의 되지만 사용자의 후속 변경 내용은 유지 됩니다.  
  
4. 그룹 섹션에서 도구 모음에 대 한 명령을 포함 하는 그룹을 정의 합니다.  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5. 단추 섹션에서 기존 단추 요소의 부모를 도구 모음 그룹으로 변경 하 여 도구 모음이 표시 되도록 합니다.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke TWTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     기본적으로 도구 모음에 명령이 없으면 표시 되지 않습니다.  
  
     새 도구 모음은 도구 창에 자동으로 추가 되지 않으므로 도구 모음을 명시적으로 추가 해야 합니다. 이에 대해서는 다음 섹션에서 설명합니다.  
  
## <a name="adding-the-toolbar-to-the-tool-window"></a>도구 창에 도구 모음 추가  
  
1. TWTestCommandPackageGuids.cs에서 다음 줄을 추가 합니다.  
  
    ```csharp  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2. TestToolWindow.cs에서 다음 using 문을 추가 합니다.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    ```  
  
3. TestToolWindow 생성자에서 다음 줄을 추가 합니다.  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## <a name="testing-the-toolbar-in-the-tool-window"></a>도구 창에서 도구 모음 테스트  
  
1. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio 실험적 인스턴스가 표시 됩니다.  
  
2. **보기/기타 창** 메뉴에서 **ToolWindow 테스트** 를 클릭 하 여 도구 창을 표시 합니다.  
  
     도구 창의 왼쪽 상단에 있는 도구 모음 (기본 아이콘 처럼 보임)이 제목 바로 아래에 표시 됩니다.  
  
3. 도구 모음에서 아이콘을 클릭 하 여 **TwMenuItemCallback () 내의 Twtestcommandpackage**메시지를 표시 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [도구 모음 추가](../extensibility/adding-a-toolbar.md)

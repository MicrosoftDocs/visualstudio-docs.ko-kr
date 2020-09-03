---
title: 메뉴 명령을 사용 하 여 확장 만들기 | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c8639ede4a01157718f0ab1a1514927e620fa8d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86972337"
---
# <a name="create-an-extension-with-a-menu-command"></a>메뉴 명령을 사용 하 여 확장 만들기

이 연습에서는 메모장을 실행 하는 메뉴 명령을 사용 하 여 확장을 만드는 방법을 보여 줍니다.

## <a name="prerequisites"></a>필수 구성 요소

Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="create-a-menu-command"></a>메뉴 명령 만들기

1. **Firstmenucommand**라는 VSIX 프로젝트를 만듭니다. **새 프로젝트** 대화 상자에서 "vsix"를 검색 하 여 vsix 프로젝트 템플릿을 찾을 수 있습니다.

::: moniker range="vs-2017"

2. 프로젝트가 열리면 **firstcommand**라는 사용자 지정 명령 항목 템플릿을 추가 합니다. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **Add**  >  **새 항목**추가를 선택 합니다. **새 항목 추가** 대화 상자에서 **Visual c #**  >  **확장성** 으로 이동 하 고 **사용자 지정 명령**을 선택 합니다. 창 맨 아래에 있는 **이름** 필드에서 명령 파일 이름을 *FirstCommand.cs*로 변경 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

2. 프로젝트가 열리면 **firstcommand**라는 사용자 지정 명령 항목 템플릿을 추가 합니다. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **Add**  >  **새 항목**추가를 선택 합니다. **새 항목 추가** 대화 상자에서 **Visual c #**  >  **확장성** 으로 이동 하 고 **명령**을 선택 합니다. 창 맨 아래에 있는 **이름** 필드에서 명령 파일 이름을 *FirstCommand.cs*로 변경 합니다.

::: moniker-end

3. 프로젝트를 빌드하고 디버깅을 시작합니다.

    Visual Studio의 실험적 인스턴스가 나타납니다. 실험적 인스턴스에 대 한 자세한 내용은 [실험적 인스턴스](../extensibility/the-experimental-instance.md)를 참조 하세요.

::: moniker range="vs-2017"

4. 실험적 인스턴스에서 **도구**  >  **확장 및 업데이트** 창을 엽니다. 여기에 **Firstmenucommand** 확장이 표시 됩니다. Visual Studio의 작업 인스턴스에서 **확장 및 업데이트** 를 열면 **firstmenucommand**가 표시 되지 않습니다.

::: moniker-end

::: moniker range=">=vs-2019"

4. 실험적 **인스턴스에서 확장**  >  **관리** 확장 창을 엽니다. 여기에 **Firstmenucommand** 확장이 표시 됩니다. Visual Studio의 작업 인스턴스에서 **확장 관리** 를 열면 **firstmenucommand**가 표시 되지 않습니다.

::: moniker-end

이제 실험적 인스턴스의 **도구** 메뉴로 이동 합니다. **FirstCommand 명령 호출** 을 확인 해야 합니다. 이 시점에서 명령은 **FirstMenuCommand MenuItemCallback () 내에 firstcommand**라는 메시지 상자를 표시 합니다. 다음 섹션에서이 명령을 실행 하 여 실제로 메모장을 시작 하는 방법을 알아봅니다.

## <a name="change-the-menu-command-handler"></a>메뉴 명령 처리기 변경

이제 명령 처리기를 업데이트 하 여 메모장을 시작 해 보겠습니다.

1. 디버깅을 중지 하 고 Visual Studio의 작업 인스턴스로 돌아갑니다. *FirstCommand.cs* 파일을 열고 다음 using 문을 추가 합니다.

    ```csharp
    using System.Diagnostics;
    ```

2. Private FirstCommand 생성자를 찾습니다. 명령이 명령 서비스로 후크 되 고 명령 처리기가 지정 되는 위치입니다. 명령 처리기의 이름을 StartNotepad로 다음과 같이 변경 합니다.

    ```csharp
    private FirstCommand(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        CommandID menuCommandID = new CommandID(CommandSet, CommandId);
        // Change to StartNotepad handler.
        MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

3. 메서드를 제거 `Execute` 하 고 메서드를 추가 합니다 `StartNotepad` .이 메서드는 메모장만 시작 합니다.

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();

        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. 이제 사용해 보세요. 프로젝트 디버깅을 시작 하 고 **도구**  >  **호출 firstcommand**를 클릭 하면 메모장의 인스턴스가 표시 됩니다.

    클래스의 인스턴스를 사용 하 여 <xref:System.Diagnostics.Process> 메모장 뿐만 아니라 실행 파일을 실행할 수 있습니다. 예를 들어를 사용 하 여 사용해 보세요 `calc.exe` .

## <a name="clean-up-the-experimental-environment"></a>실험적 환경 정리

여러 확장을 개발 하거나 확장 코드의 다른 버전을 사용 하 여 결과를 탐색 하는 경우 실험 환경에서 작동 하지 않을 수 있습니다. 이 경우 다시 설정 스크립트를 실행 해야 합니다. **Visual Studio 실험적 인스턴스를 다시 설정**하 고 VISUAL studio SDK의 일부로 제공 됩니다. 이 스크립트는 실험적 환경에서 확장에 대 한 모든 참조를 제거 하므로 처음부터 시작할 수 있습니다.

이 스크립트는 다음 두 가지 방법 중 하나로 가져올 수 있습니다.

1. 바탕 화면에서 **Visual Studio 실험적 인스턴스 다시 설정**을 찾습니다.

2. 명령줄에서 다음을 실행하세요.

    ```cmd
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>확장 배포

원하는 방식으로 도구 확장을 실행 했으므로 친구 및 동료와 공유 하는 것에 대해 생각해 보겠습니다. Visual Studio 2015가 설치 된 경우에는 쉽게 수행할 수 있습니다. 사용자가 빌드한 *.vsix* 파일을 전송 하면 됩니다. (릴리스 모드에서 빌드해야 합니다.)

이 확장에 대 한 *.vsix* 파일은 *firstmenucommand* bin 디렉터리에서 찾을 수 있습니다. 특히 릴리스 구성을 빌드한 경우에는 다음 위치에 있습니다.

*\<code directory>\FirstMenuCommand\FirstMenuCommand\bin\Release\FirstMenuCommand.vsix*

확장을 설치 하려면 *친구는 Visual* Studio의 모든 열린 인스턴스를 닫은 다음 vsix 파일을 두 번 클릭 하 여 **vsix 설치 관리자**를 표시 해야 합니다. 파일이 *%LocalAppData%\Microsoft\VisualStudio \<version> \extensions* 디렉터리에 복사 됩니다.

친구가 Visual Studio를 다시 시작 하면 **도구**  >  **확장 및 업데이트**에서 firstmenucommand 확장을 찾을 수 있습니다. 확장 **및 업데이트로** 이동 하 여 확장을 제거 하거나 사용 하지 않도록 설정할 수 있습니다.

## <a name="next-steps"></a>다음 단계

이 연습에서는 Visual Studio 확장을 사용 하 여 수행할 수 있는 작업 중 일부만 표시 했습니다. 다음은 Visual Studio 확장을 사용 하 여 수행할 수 있는 간단한 다른 작업 목록입니다.

1. 간단한 메뉴 명령을 사용 하 여 더 많은 작업을 수행할 수 있습니다.

   1. 사용자 고유의 아이콘 추가: [메뉴 명령에 아이콘 추가](../extensibility/adding-icons-to-menu-commands.md)

   2. 메뉴 명령의 텍스트를 변경 합니다. [메뉴 명령의 텍스트를 변경](../extensibility/changing-the-text-of-a-menu-command.md) 합니다.

   3. 명령에 메뉴 바로 가기 추가: [메뉴 항목에 바로 가기 키 바인딩](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. 다양 한 종류의 명령, 메뉴 및 도구 모음 추가: [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)

3. 도구 창을 추가 하 고 기본 제공 Visual Studio 도구 창 확장: [도구 창 확장 및 사용자 지정](../extensibility/extending-and-customizing-tool-windows.md)

4. 기존 코드 편집기에 IntelliSense, 코드 제안 및 기타 기능 추가: [편집기 및 언어 서비스 확장](../extensibility/extending-the-editor-and-language-services.md)

5. 옵션 및 속성 페이지 및 사용자 설정을 확장에 추가: [속성 및 속성 창을 확장](../extensibility/extending-properties-and-the-property-window.md) 하 고 [사용자 설정 및 옵션을 확장](../extensibility/extending-user-settings-and-options.md) 합니다.

   다른 종류의 확장 프로그램을 사용 하려면 새 프로젝트 형식 만들기 ([프로젝트 확장](../extensibility/extending-projects.md)), 새 편집기 유형 만들기 ([사용자 지정 편집기 및 디자이너 만들기](../extensibility/creating-custom-editors-and-designers.md)) 또는 격리 된 셸에서 확장을 구현 하는 것과 같이 좀 더 많은 작업이 필요 합니다. [Visual Studio 격리 셸](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

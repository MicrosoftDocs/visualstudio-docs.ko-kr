---
title: 메뉴 명령으로 확장 만들기 | 마이크로 소프트 문서
ms.date: 3/16/2019
ms.topic: conceptual
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
ms.openlocfilehash: da1be8c6e00efd5d9ac94e53bf551d82d0f17ca4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739552"
---
# <a name="create-an-extension-with-a-menu-command"></a>메뉴 명령으로 확장 만들기

이 연습에서는 메모장을 실행 하는 메뉴 명령을 사용하여 확장을 만드는 방법을 보여 줍니다.

## <a name="prerequisites"></a>사전 요구 사항

Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. 시각적 스튜디오 설정에서 선택적 기능으로 포함됩니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-a-menu-command"></a>메뉴 명령 만들기

1. **FirstMenuCommand이라는**VSIX 프로젝트를 만듭니다. 새 프로젝트 대화 상자에서 "vsix"를 검색하여 VSIX **프로젝트** 템플릿을 찾을 수 있습니다.

2. 프로젝트가 열리면 **FirstCommand**이라는 사용자 지정 명령 항목 템플릿을 추가합니다. 솔루션 **탐색기에서**프로젝트 노드를 마우스 오른쪽 단추로 클릭하고**새 항목** **추가를** > 선택합니다. 새 **항목 추가** 대화 상자에서 **시각적 C#** > **확장성으로** 이동하여 **사용자 지정 명령을 선택합니다.** 창 아래쪽의 **이름** 필드에서 명령 파일 이름을 *FirstCommand.cs.*

3. 프로젝트를 빌드하고 디버깅을 시작합니다.

    Visual Studio의 실험 인스턴스가 나타납니다. 실험 인스턴스에 대한 자세한 내용은 [실험 인스턴스 를](../extensibility/the-experimental-instance.md)참조하십시오.

::: moniker range="vs-2017"

4. 실험 인스턴스에서 **도구** > 확장 및 업데이트 창을**엽니다.** **FirstMenuCommand** 확장은 여기에 표시됩니다. (Visual Studio의 작업 인스턴스에서 **확장 및 업데이트를** 열면 **FirstMenuCommand이**표시되지 않습니다.)

::: moniker-end

::: moniker range=">=vs-2019"

4. 실험 인스턴스에서 **확장** > 관리 창을**엽니다.** **FirstMenuCommand** 확장은 여기에 표시됩니다. (Visual Studio의 작업 인스턴스에서 **확장 관리를** 열면 **FirstMenuCommand이**표시되지 않습니다.)

::: moniker-end

이제 실험 인스턴스의 **도구** 메뉴로 이동합니다. **FirstCommand 호출** 명령이 표시됩니다. 이 시점에서 명령은 **FirstMenuCommand.FirstCommand.MenuItemCallback() 내부에 FirstCommandPackage를**라는 메시지 상자를 제공합니다. 다음 섹션에서 이 명령에서 메모장을 실제로 시작하는 방법을 살펴보겠습니다.

## <a name="change-the-menu-command-handler"></a>메뉴 명령 처리기 변경

이제 메모장을 시작하려면 명령 처리기를 업데이트해 보겠습니다.

1. 디버깅을 중지하고 Visual Studio의 작업 인스턴스로 돌아갑니다. *FirstCommand.cs* 파일을 열고 다음 을 사용하여 다음을 추가합니다.

    ```csharp
    using System.Diagnostics;
    ```

2. 개인 FirstCommand 생성자 찾기 여기서 명령이 명령 서비스에 연결되고 명령 처리기가 지정됩니다. 다음과 같이 명령 처리기의 이름을 StartNotepad로 변경합니다.

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

3. 메서드를 `MenuItemCallback` 제거하고 메모장을 시작하는 메서드를 `StartNotepad` 추가합니다.

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. 이제 그것을 밖으로 시도. 프로젝트 디버깅을 시작하고 **도구** > **호출 FirstCommand을**클릭하면 메모장의 인스턴스가 표시됩니다.

    클래스의 인스턴스를 <xref:System.Diagnostics.Process> 사용하여 메모장뿐만 아니라 실행 가능한 모든 실행 을 실행할 수 있습니다. 예를 들어 `calc.exe`.와 함께 사용해 보십시오.

## <a name="clean-up-the-experimental-environment"></a>실험 환경 정리

여러 확장을 개발하거나 다른 버전의 확장 코드로 결과를 탐색하는 경우 실험 환경이 원하는 방식으로 작동하지 않을 수 있습니다. 이 경우 리셋 스크립트를 실행해야 합니다. 비주얼 스튜디오 **실험 인스턴스 재설정이라고**하며 Visual Studio SDK의 일부로 제공됩니다. 이 스크립트는 실험 환경에서 확장에 대한 모든 참조를 제거하므로 처음부터 시작할 수 있습니다.

다음 두 가지 방법 중 하나로 이 스크립트를 사용할 수 있습니다.

1. 바탕 화면에서 **Visual Studio 실험 인스턴스 재설정**을 찾습니다.

2. 명령줄에서 다음을 실행하세요.

    ```xml
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>확장 배포

이제 도구 확장 프로그램이 원하는 방식으로 실행되었으므로 친구 및 동료와 공유하는 방법을 생각해 볼 차례입니다. Visual Studio 2015가 설치되어 있는 한 간단합니다. 당신이해야 할 모든 그들에게 당신이 만든 *.vsix* 파일을 보내입니다. 릴리스 모드에서 빌드해야 합니다.

이 확장명에 대한 *.vsix* 파일은 *FirstMenuCommand* 빈 디렉토리에서 찾을 수 있습니다. 특히 릴리스 구성을 빌드했다고 가정하면 다음 이 에 있을 것입니다.

*\<코드 디렉토리>\FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix*

확장을 설치하려면 친구가 Visual Studio의 열려 있는 모든 인스턴스를 닫은 다음 *.vsix* 파일을 두 번 클릭하여 **VSIX 설치 관리자를**불러옵니다. 파일은 *%LocalAppData%\Microsoft\VisualStudio\<버전>\확장 디렉토리에 복사됩니다.*

친구가 Visual Studio를 다시 불러오면 **도구** > **확장 및 업데이트에서**FirstMenuCommand 확장을 찾을 수 있습니다. 확장 및 **업데이트로** 이동하여 확장을 제거하거나 비활성화할 수도 있습니다.

## <a name="next-steps"></a>다음 단계

이 연습에서는 Visual Studio 확장을 통해 수행할 수 있는 작업의 일부만 보여 주실 수 있습니다. 다음은 Visual Studio 확장으로 수행할 수 있는 다른(합리적으로 쉬운) 작업의 짧은 목록입니다.

1. 간단한 메뉴 명령으로 더 많은 작업을 수행할 수 있습니다.

   1. 나만의 아이콘 추가: [메뉴 명령에 아이콘 추가](../extensibility/adding-icons-to-menu-commands.md)

   2. 메뉴 명령의 텍스트 변경: [메뉴 명령의 텍스트 변경](../extensibility/changing-the-text-of-a-menu-command.md)

   3. 명령에 메뉴 바로 가기 추가: [키보드 단축키를 메뉴 항목에 바인딩합니다.](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. 다양한 종류의 명령, 메뉴 및 도구 모음 추가: [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)

3. 도구 창을 추가하고 기본 제공 Visual Studio 도구 창을 확장합니다: [도구 창을 확장 및 사용자 지정](../extensibility/extending-and-customizing-tool-windows.md)

4. 기존 코드 편집기에 IntelliSense, 코드 제안 및 기타 기능 추가: [편집기 및 언어 서비스 확장](../extensibility/extending-the-editor-and-language-services.md)

5. 확장에 옵션 및 속성 페이지 및 사용자 설정 추가: [속성 및 속성 창 확장](../extensibility/extending-properties-and-the-property-window.md) 및 사용자 설정 및 옵션 [확장](../extensibility/extending-user-settings-and-options.md)

   다른 종류의 확장에는 새 유형의 프로젝트[만들기(프로젝트 확장),](../extensibility/extending-projects.md)새 유형의 편집기 만들기(사용자[지정 편집기 및 디자이너 만들기)](../extensibility/creating-custom-editors-and-designers.md)또는 격리된 셸에서 확장 [구현과](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/) 같은 추가 작업이 필요합니다.

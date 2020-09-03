---
title: 상태 표시줄 확장 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa62326d82d81f7ee4d10a838209364355cc488e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711547"
---
# <a name="extend-the-status-bar"></a>상태 표시줄 확장
IDE 하단에 있는 Visual Studio 상태 표시줄을 사용 하 여 정보를 표시할 수 있습니다.

 상태 표시줄을 확장 하면 사용자 의견 영역, 진행률 표시줄, 애니메이션 영역 및 디자이너 영역의 4 개 지역에 정보 및 UI를 표시할 수 있습니다. 사용자 의견 영역에서 텍스트를 표시 하 고 표시 된 텍스트를 강조할 수 있습니다. 진행률 표시줄에는 파일 저장과 같은 단기 실행 작업의 증분 진행률이 표시 됩니다. 애니메이션 영역에는 솔루션에서 여러 프로젝트를 빌드하는 것과 같이 장기 실행 작업 또는 결정 되지 않은 길이의 작업에 대해 지속적으로 반복 되는 애니메이션이 표시 됩니다. 그리고 디자이너 영역은 커서 위치의 줄 및 열 번호를 표시 합니다.

 서비스에서 인터페이스를 사용 하 여 상태 표시줄을 가져올 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> . 또한 창 프레임에 있는 모든 개체는 인터페이스를 구현 하 여 상태 표시줄 클라이언트 개체로 등록할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> . 창이 활성화 될 때마다 Visual Studio는 해당 창에서 인터페이스에 대 한 개체를 쿼리 `IVsStatusbarUser` 합니다. 찾은 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> 반환 된 인터페이스에서 메서드를 호출 하 고 개체는 해당 메서드 내에서 상태 표시줄을 업데이트할 수 있습니다. 예를 들어, 문서 창에서는 메서드를 사용 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> 하 여 디자이너 영역에서 활성화 될 때 정보를 업데이트할 수 있습니다.

 다음 절차에서는 VSIX 프로젝트를 만들고 사용자 지정 메뉴 명령을 추가 하는 방법을 이해 하 고 있다고 가정 합니다. 자세한 내용은 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)를 참조 하세요.

## <a name="modify-the-status-bar"></a>상태 표시줄 수정
 이 절차에서는 텍스트를 설정 및 가져오고, 정적 텍스트를 표시 하 고, 상태 표시줄의 피드백 영역에서 표시 된 텍스트를 강조 표시 하는 방법을 보여 줍니다.

### <a name="read-and-write-to-the-status-bar"></a>상태 표시줄에 대 한 읽기 및 쓰기

1. **TestStatusBarExtension** 라는 VSIX 프로젝트를 만들고 **TestStatusBarCommand**라는 메뉴 명령을 추가 합니다.

2. *TestStatusBarCommand.cs*에서 명령 처리기 메서드 코드 ( `MenuItemCallback` )를 다음으로 바꿉니다.

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Make sure the status bar is not frozen
        int frozen;

        statusBar.IsFrozen(out frozen);

        if (frozen != 0)
        {
            statusBar.FreezeOutput(0);
        }

        // Set the status bar text and make its display static.
        statusBar.SetText("We just wrote to the status bar.");

        // Freeze the status bar.
        statusBar.FreezeOutput(1);

        // Get the status bar text.
        string text;
        statusBar.GetText(out text);
        System.Windows.Forms.MessageBox.Show(text);

        // Clear the status bar text.
        statusBar.FreezeOutput(0);
        statusBar.Clear();
    }
    ```

3. 코드를 컴파일하고 디버깅을 시작 합니다.

4. Visual Studio의 실험적 인스턴스에서 **도구** 메뉴를 엽니다. **Invoke TestStatusBarCommand** 단추를 클릭 합니다.

     상태 표시줄의 텍스트는 이제 **상태 표시줄에 작성** 한 것을 확인 해야 합니다. 표시 되는 메시지 상자의 텍스트는 동일 합니다.

### <a name="update-the-progress-bar"></a>진행률 표시줄 업데이트

1. 이 절차에서는 진행률 표시줄을 초기화 하 고 업데이트 하는 방법을 보여 줍니다.

2. *TestStatusBarCommand.cs* 파일을 열고 `MenuItemCallback` 메서드를 다음 코드로 바꿉니다.

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));
        uint cookie = 0;
        string label = "Writing to the progress bar";

        // Initialize the progress bar.
        statusBar.Progress(ref cookie, 1, "", 0, 0);

        for (uint i = 0, total = 20; i <= total; i++)
        {
            // Display progress every second.
            statusBar.Progress(ref cookie, 1, label, i, total);
            System.Threading.Thread.Sleep(1000);
        }

        // Clear the progress bar.
        statusBar.Progress(ref cookie, 0, "", 0, 0);
    }
    ```

3. 코드를 컴파일하고 디버깅을 시작 합니다.

4. Visual Studio의 실험적 인스턴스에서 **도구** 메뉴를 엽니다. **TestStatusBarCommand 호출** 단추를 클릭 합니다.

     이제 상태 표시줄의 텍스트가 **진행률 표시줄에 쓰기를** 읽도록 표시 되어야 합니다. 또한 20 초 마다 진행률 표시줄이 업데이트 됩니다. 그러면 상태 표시줄 및 진행률 표시줄이 지워집니다.

### <a name="display-an-animation"></a>애니메이션 표시

1. 상태 표시줄에는 장기 실행 작업 (예: 솔루션에서 여러 프로젝트 빌드)을 나타내는 반복 애니메이션이 표시 됩니다. 이 애니메이션이 표시 되지 않으면 올바른 **도구**  >  **옵션** 설정을 사용 하도록 설정 해야 합니다.

     **도구**  >  **옵션**  >  **일반** 탭으로 이동 하 여 **클라이언트 성능에 따라 시각적 효과 자동 조정**의 선택을 취소 합니다. 그런 다음 하위 옵션인 **리치 클라이언트 시각적 효과 사용**을 선택 합니다. 이제 Visual Studio의 실험적 인스턴스에서 프로젝트를 빌드할 때 애니메이션을 볼 수 있습니다.

     이 절차에서는 프로젝트 또는 솔루션 빌드를 나타내는 표준 Visual Studio 애니메이션을 표시 합니다.

2. *TestStatusBarCommand.cs* 파일을 열고 `MenuItemCallback` 메서드를 다음 코드로 바꿉니다.

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Use the standard Visual Studio icon for building.
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;

        // Display the icon in the Animation region.
        statusBar.Animation(1, ref icon);

        // The message box pauses execution for you to look at the animation.
        System.Windows.Forms.MessageBox.Show("showing?");

        // Stop the animation.
        statusBar.Animation(0, ref icon);
    }
    ```

3. 코드를 컴파일하고 디버깅을 시작 합니다.

4. Visual Studio의 실험적 인스턴스에서 **도구** 메뉴를 열고 **TestStatusBarCommand 호출**을 클릭 합니다.

     메시지 상자가 표시 되 면 맨 오른쪽의 상태 표시줄에도 애니메이션이 표시 되어야 합니다. 메시지 상자를 닫으면 애니메이션이 사라집니다.

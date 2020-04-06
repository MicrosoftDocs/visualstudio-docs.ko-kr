---
title: 상태 표시줄 확장 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711547"
---
# <a name="extend-the-status-bar"></a>상태 표시줄 확장
IDE 하단의 Visual Studio 상태 표시줄을 사용하여 정보를 표시할 수 있습니다.

 상태 표시줄을 확장하면 피드백 영역, 진행률 표시줄, 애니메이션 영역 및 디자이너 영역의 네 가지 영역에 정보와 UI를 표시할 수 있습니다. 피드백 영역을 사용하면 텍스트를 표시하고 표시된 텍스트를 강조 표시할 수 있습니다. 진행률 표시줄에는 파일 저장과 같은 단기 실행 작업에 대한 증분 진행률을 표시합니다. 애니메이션 영역에는 솔루션에서 여러 프로젝트를 빌드하는 것과 같이 장기 실행 작업 또는 미정 길이의 작업을 위해 연속 루프 애니메이션이 표시됩니다. 디자이너 영역은 커서 위치의 선 및 열 번호를 표시합니다.

 <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> (서비스에서) 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> 사용 하 여 상태 표시줄을 얻을 수 있습니다. 또한 창 프레임에 사이트에 있는 모든 개체는 인터페이스를 구현하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> 상태 표시줄 클라이언트 개체로 등록할 수 있습니다. 창이 활성화될 때마다 Visual Studio는 인터페이스에 대해 해당 `IVsStatusbarUser` 창에 있는 개체를 쿼리합니다. 발견되면 반환된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> 인터페이스에서 메서드를 호출하고 개체는 해당 메서드 내에서 상태 표시줄을 업데이트할 수 있습니다. 예를 들어 문서 창은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> 이 메서드를 사용하여 디자이너 영역의 정보가 활성화될 때 업데이트할 수 있습니다.

 다음 절차에서는 VSIX 프로젝트를 만들고 사용자 지정 메뉴 명령을 추가하는 방법을 이해한다고 가정합니다. 자세한 내용은 [메뉴 명령을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-menu-command.md)참조하십시오.

## <a name="modify-the-status-bar"></a>상태 표시줄 수정
 이 절차에서는 상태 표시줄의 피드백 영역에서 텍스트를 설정하고 받고, 정적 텍스트를 표시하고, 표시된 텍스트를 강조 표시하는 방법을 보여 주었습니다.

### <a name="read-and-write-to-the-status-bar"></a>상태 표시줄에 읽기 및 쓰기

1. **테스트 상태BarExtension이라는** VSIX 프로젝트를 만들고 **TestStatusBarCommand라는**메뉴 명령을 추가합니다.

2. *TestStatusBarCommand.cs*명령 처리기 메서드 코드`MenuItemCallback`() 를 다음과 같은 값으로 바꿉니다.

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

3. 코드를 컴파일하고 디버깅을 시작합니다.

4. Visual Studio의 실험 인스턴스에서 **도구** 메뉴를 엽니다. 테스트 **상태 BarCommand 호출** 단추를 클릭합니다.

     상태 표시줄의 텍스트가 이제 **상태 표시줄에 방금 쓴** 것으로 표시됩니다. 표시되는 메시지 상자에 동일한 텍스트가 있습니다.

### <a name="update-the-progress-bar"></a>진행률 표시줄 업데이트

1. 이 절차에서는 진행률 표시줄을 초기화하고 업데이트하는 방법을 보여 드리겠습니다.

2. *TestStatusBarCommand.cs* 파일을 열고 메서드를 `MenuItemCallback` 다음 코드로 바꿉니다.

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

3. 코드를 컴파일하고 디버깅을 시작합니다.

4. Visual Studio의 실험 인스턴스에서 **도구** 메뉴를 엽니다. **테스트 상태 바명령 호출 단추를 클릭합니다.**

     상태 표시줄의 텍스트가 **진행률 표시줄에 쓰기를** 읽는 것을 볼 수 있습니다. 또한 진행률 표시줄이 20초 동안 매초 업데이트되는 것을 볼 수 있습니다. 그 후 상태 표시줄과 진행률 표시줄이 지워집니다.

### <a name="display-an-animation"></a>애니메이션 표시

1. 상태 표시줄에는 장기 실행 작업(예: 솔루션에서 여러 프로젝트 빌드)을 나타내는 루핑 애니메이션이 표시됩니다. 이 애니메이션이 표시되지 않으면 **도구** > **옵션** 설정이 올바른지 확인하십시오.

     **도구** > **옵션** > **일반** 탭으로 이동하여 **클라이언트 성능에 따라 시각적 환경을 자동으로 조정취소합니다.** 그런 다음 하위 옵션을 **확인하여 풍부한 클라이언트 시각적 환경 활성화.** 이제 실험적인 Visual Studio 인스턴스에서 프로젝트를 빌드할 때 애니메이션을 볼 수 있습니다.

     이 절차에서는 프로젝트 또는 솔루션 빌드를 나타내는 표준 Visual Studio 애니메이션을 표시합니다.

2. *TestStatusBarCommand.cs* 파일을 열고 메서드를 `MenuItemCallback` 다음 코드로 바꿉니다.

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

3. 코드를 컴파일하고 디버깅을 시작합니다.

4. 시각적 스튜디오의 실험 인스턴스에서 **도구** 메뉴를 열고 **호출 테스트 StatusBarCommand를**클릭합니다.

     메시지 상자가 표시되면 맨 오른쪽에 있는 상태 표시줄에도 애니메이션이 표시됩니다. 메시지 상자를 해제하면 애니메이션이 사라집니다.

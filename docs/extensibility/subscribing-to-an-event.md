---
title: 이벤트 구독 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6aefe2efce897aefc26f63835844b0cc705fb5b1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699690"
---
# <a name="subscribing-to-an-event"></a>이벤트 구독
이 연습에서는 실행 중인 문서 테이블(RDT)의 이벤트에 응답하는 도구 창을 만드는 방법을 설명합니다. 도구 창은 을 구현하는 사용자 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>컨트롤을 호스트합니다. 메서드는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> 이벤트에 인터페이스를 연결 합니다.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. 시각적 스튜디오 설정에서 선택적 기능으로 포함됩니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="subscribing-to-rdt-events"></a>RDT 이벤트 구독

#### <a name="to-create-an-extension-with-a-tool-window"></a>도구 창을 사용하여 확장을 만들려면

1. VSIX 템플릿을 사용하여 **RDTExplorer라는** 프로젝트를 만들고 **RDTExplorerWindow라는**사용자 지정 도구 창 항목 템플릿을 추가합니다.

     도구 창을 사용하여 확장을 만드는 자세한 내용은 [도구 창을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-tool-window.md)참조하십시오.

#### <a name="to-subscribe-to-rdt-events"></a>RDT 이벤트를 구독하려면

1. RDTExplorerWindowControl.xaml 파일을 열고 라는 `button1`단추를 삭제합니다. 컨트롤을 <xref:System.Windows.Forms.ListBox> 추가하고 기본 이름을 수락합니다. 그리드 요소는 다음과 같아야 합니다.

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. 코드 보기에서 RDTExplorerWindow.cs 파일을 엽니다. 지시문을 사용하여 다음을 파일의 시작 부분에 추가합니다.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. 클래스에서 `RDTExplorerWindow` 파생 하는 것 외에도 인터페이스를 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> 구현 하도록 클래스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> 수정 합니다.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>를 구현해야 합니다.

    - 인터페이스를 구현합니다. IVRunningDocTableEvents 이름에 커서를 배치합니다. 왼쪽 여백에 전구가 표시됩니다. 전구 오른쪽의 아래쪽 화살표를 클릭하고 **인터페이스 구현을**선택합니다.

5. 인터페이스의 각 메서드에서 선을 `throw new NotImplementedException();` 다음과 같은 것으로 바꿉꿉을 사용합니다.

    ```csharp
    return VSConstants.S_OK;
    ```

6. RDTExplorerWindow 클래스에 쿠키 필드를 추가합니다.

    ```csharp
    private uint rdtCookie;
    ```

     메서드에 의해 반환 되는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> 쿠키를 보유 합니다.

7. RDT 이벤트에 등록하려면 RDTExplorerWindow의 초기화() 메서드를 재정의합니다. 생성자가 아닌 ToolWindowPane의 초기화() 메서드에서 항상 서비스를 받아야 합니다.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> 얻기 위해 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> 서비스가 호출됩니다. 메서드는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> RDT 이벤트를 구현하는 개체에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>연결합니다.

8. RDT익스플로러윈도우의 Dispose() 메서드를 업데이트합니다.

    ```csharp
    protected override void Dispose(bool disposing)
    {
        // Release the RDT cookie.
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));
        rdt.UnadviseRunningDocTableEvents(rdtCookie);

        base.Dispose(disposing);
    }
    ```

     이 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> 메서드는 RDT `RDTExplorer` 이벤트 알림 사이의 연결을 삭제합니다.

9. 명령문 바로 앞의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> 처리기 본문에 `return` 다음 줄을 추가합니다.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> 처리기 의 본문 과 목록 상자에 표시 하려는 다른 이벤트에 비슷한 줄을 추가 합니다.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. 프로젝트를 빌드하고 디버깅을 시작합니다. 비주얼 스튜디오 실험 인스턴스가 나타납니다.

12. **RDT익스플로러윈도우** **(보기 / 기타 윈도우 / RDT익스플로러윈도우)를**엽니다.

     **RDTExplorerWindow** 창이 빈 이벤트 목록으로 열립니다.

13. 솔루션을 열거나 만듭니다.

     `OnBeforeLastDocument` 이벤트가 발생하면 각 이벤트에 대한 알림이 이벤트 목록에 `OnAfterFirstDocument` 나타납니다.

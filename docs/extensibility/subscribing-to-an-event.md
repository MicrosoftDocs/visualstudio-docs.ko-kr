---
title: 이벤트 | 구독 Microsoft Docs
description: Visual Studio SDK에서 실행 중인 문서 테이블의 이벤트에 응답하는 도구 창을 만드는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 01271016eed9a4a157b333a2f0435589b0a028d5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899395"
---
# <a name="subscribing-to-an-event"></a>이벤트 구독
이 연습에서는 실행 중인 RDT(문서 테이블)에서 이벤트에 응답하는 도구 창을 만드는 방법을 설명합니다. 도구 창은 를 구현하는 사용자 컨트롤을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> 호스팅합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>메서드는 인터페이스를 이벤트에 연결합니다.

## <a name="prerequisites"></a>필수 구성 요소
 Visual Studio 2015부터 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. Visual Studio 설정에 선택적 기능으로 포함되어 있습니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를 참조하세요.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="subscribing-to-rdt-events"></a>RDT 이벤트 구독

#### <a name="to-create-an-extension-with-a-tool-window"></a>도구 창을 사용하여 확장을 만들려면

1. VSIX 템플릿을 사용하여 **RDTExplorer라는** 프로젝트를 만들고 **RDTExplorerWindow라는** 사용자 지정 도구 창 항목 템플릿을 추가합니다.

     도구 창을 사용하여 확장을 만드는 자세한 내용은 도구 창을 [사용하여 확장 만들기를 참조하세요.](../extensibility/creating-an-extension-with-a-tool-window.md)

#### <a name="to-subscribe-to-rdt-events"></a>RDT 이벤트를 구독하려면

1. RDTExplorerWindowControl.xaml 파일을 열고 라는 단추를 `button1` 삭제합니다. <xref:System.Windows.Forms.ListBox>컨트롤을 추가하고 기본 이름을 적용합니다. Grid 요소는 다음과 같습니다.

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. 코드 보기에서 RDTExplorerWindow.cs 파일을 엽니다. 파일의 시작 부분에 다음 using 지시문을 추가합니다.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. `RDTExplorerWindow`클래스에서 파생되는 것 외에도 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> 인터페이스를 구현하도록 클래스를 수정합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>를 구현해야 합니다.

    - 인터페이스를 구현합니다. IVsRunningDocTableEvents 이름에 커서를 놓습니다. 왼쪽 여백에 전구가 표시됩니다. 전구 오른쪽의 아래쪽 화살표를 클릭하고 **인터페이스 구현을** 선택합니다.

5. 인터페이스의 각 메서드에서 줄을 다음으로 대체합니다. `throw new NotImplementedException();`

    ```csharp
    return VSConstants.S_OK;
    ```

6. RDTExplorerWindow 클래스에 쿠키 필드를 추가합니다.

    ```csharp
    private uint rdtCookie;
    ```

     이 메서드는 메서드에서 반환되는 쿠키를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> 보유합니다.

7. RDT 이벤트를 등록하려면 RDTExplorerWindow의 Initialize() 메서드를 재정의합니다. 항상 생성자가 아닌 ToolWindowPane의 Initialize() 메서드에서 서비스를 받아야 합니다.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>서비스는 인터페이스를 얻기 위해 호출됩니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>메서드는 RDT 이벤트를 구현하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> 개체(이 경우 RDTExplorer 개체)에 연결합니다.

8. RDTExplorerWindow의 Dispose() 메서드를 업데이트합니다.

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

     <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A>메서드는 와 RDT 이벤트 알림 간의 연결을 `RDTExplorer` 삭제합니다.

9. 문 바로 앞의 처리기 본문에 다음 줄을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> `return` 추가합니다.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. 처리기의 본문과 목록 상자에 표시할 다른 이벤트에 유사한 줄을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> 추가합니다.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio 실험적 인스턴스가 나타납니다.

12. **RDTExplorerWindow를** **엽니다(보기/기타 창/RDTExplorerWindow).**

     **RDTExplorerWindow** 창이 빈 이벤트 목록과 함께 열립니다.

13. 솔루션을 열거나 만듭니다.

     `OnBeforeLastDocument`및 `OnAfterFirstDocument` 이벤트가 발생하면 각 이벤트에 대한 알림이 이벤트 목록에 표시됩니다.

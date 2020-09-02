---
title: 이벤트 구독 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 324e74c78f01da47c544b5f640ad0bd9052a1bb4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160551"
---
# <a name="subscribing-to-an-event"></a>이벤트 구독
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 RDT (실행 문서 테이블)에서 이벤트에 응답 하는 도구 창을 만드는 방법을 설명 합니다. 도구 창은을 구현 하는 사용자 정의 컨트롤을 호스팅합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>메서드는 인터페이스를 이벤트에 연결 합니다.  
  
## <a name="prerequisites"></a>사전 준비 사항  
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.  
  
## <a name="subscribing-to-rdt-events"></a>RDT 이벤트 구독  
  
#### <a name="to-create-an-extension-with-a-tool-window"></a>도구 창을 사용 하 여 확장을 만들려면  
  
1. VSIX 템플릿을 사용 하 여 **RDTExplorer** 이라는 프로젝트를 만들고 **RDTExplorerWindow**라는 사용자 지정 도구 창 항목 템플릿을 추가 합니다.  
  
     도구 창을 사용 하 여 확장을 만드는 방법에 대 한 자세한 내용은 [도구 창을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-tool-window.md)를 참조 하세요.  
  
#### <a name="to-subscribe-to-rdt-events"></a>RDT 이벤트를 구독 하려면  
  
1. RDTExplorerWindowControl 파일을 열고 이라는 단추를 삭제 `button1` 합니다. 컨트롤을 추가 <xref:System.Windows.Forms.ListBox> 하 고 기본 이름을 적용 합니다. Grid 요소는 다음과 같습니다.  
  
    ```xml  
    <Grid>  
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">  
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>  
            <ListBox x:Name="listBox" Height="100" />  
        </StackPanel>  
    </Grid>  
    ```  
  
2. 코드 보기에서 RDTExplorerWindow.cs 파일을 엽니다. 파일의 시작 부분에 다음 using 문을 추가 합니다.  
  
    ```csharp  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3. 클래스 `RDTExplorerWindow` 에서 파생 되는 것 외에도 인터페이스를 구현 하도록 클래스를 수정 합니다 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> .  
  
    ```csharp  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents  
    {. . .}  
    ```  
  
4. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>를 구현해야 합니다.  
  
    - 인터페이스를 구현 합니다. IVsRunningDocTableEvents 이름에 커서를 놓습니다. 왼쪽 여백에 전구가 표시 되어야 합니다. 전구 오른쪽에 있는 아래쪽 화살표를 클릭 하 고 **인터페이스 구현**을 선택 합니다.  
  
5. 인터페이스의 각 메서드에서 줄을 `throw new NotImplementedException();` 다음으로 바꿉니다.  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
6. RDTExplorerWindow 클래스에 쿠키 필드를 추가 합니다.  
  
    ```csharp  
    private uint rdtCookie;   
    ```  
  
     메서드에 의해 반환 되는 쿠키를 저장 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> .  
  
7. RDTExplorerWindow의 Initialize () 메서드를 재정의 하 여 RDT 이벤트에 등록 합니다. 항상 생성자가 아닌 ToolWindowPane의 Initialize () 메서드에서 서비스를 가져와야 합니다.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
        this.GetService(typeof(SVsRunningDocumentTable));  
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);  
    }  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>서비스를 호출 하 여 인터페이스를 가져옵니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>메서드는 RDT 이벤트를 구현 하는 개체 ( <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> 이 경우 RDTExplorer 개체)에 연결 합니다.  
  
8. RDTExplorerWindow의 Dispose () 메서드를 업데이트 합니다.  
  
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
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A>메서드는 `RDTExplorer` 와 rdt 이벤트 알림 간에 연결을 삭제 합니다.  
  
9. 문 바로 앞에 있는 처리기의 본문에 다음 줄을 추가 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> `return` .  
  
    ```csharp  
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
10. 처리기의 본문과 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> 목록 상자에 표시 하려는 다른 이벤트에 유사한 줄을 추가 합니다.  
  
    ```csharp  
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
11. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio 실험적 인스턴스가 나타납니다.  
  
12. **RDTExplorerWindow** (**View/Other Windows/RDTExplorerWindow**)를 엽니다.  
  
     빈 이벤트 목록이 포함 된 **RDTExplorerWindow** 창이 열립니다.  
  
13. 솔루션을 열거나 만듭니다.  
  
     `OnBeforeLastDocument`및 `OnAfterFirstDocument` 이벤트가 발생 하면 각 이벤트의 알림이 이벤트 목록에 표시 됩니다.

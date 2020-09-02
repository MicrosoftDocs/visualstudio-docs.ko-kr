---
title: 편집기 어댑터에서 새로 발생 하거나 변경 된 동작 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc7ddaf7ec67a1e33248d5ce424868849200d3e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194172"
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>편집기 어댑터를 사용하는 새롭거나 변경된 동작
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이전 버전의 Visual Studio core 편집기에 대해 작성 된 코드를 업데이트 하는 경우 새 API를 사용 하는 대신 편집기 어댑터 (또는 shim)를 사용 하려는 경우 이전 핵심 편집기와 관련 하 여 편집기 어댑터의 동작에서 다음과 같은 차이점을 알고 있어야 합니다.  
  
## <a name="features"></a>기능  
  
#### <a name="using-setsite"></a>SetSite () 사용  
 <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A>텍스트 버퍼, 텍스트 뷰 및 코드 창에서 다른 작업을 수행 하기 전에 CoCreate를 호출 해야 합니다. 그러나 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> 이 서비스의 create () 메서드 자체가를 호출 하기 때문에를 사용 하 여 만드는 경우에는이 작업이 필요 하지 않습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A> .  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>사용자 고유의 콘텐츠에서 IVsCodeWindow 및 Ivscodewindow 호스팅  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> WIN32 모드나 WPF 모드를 사용 하 여 사용자 고유의 콘텐츠에서 및를 모두 호스트할 수 있습니다. 그러나 두 모드에서 약간의 차이가 있다는 점에 유의 해야 합니다.  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>Win32 및 WPF 버전의 IVsCodeWindow 사용  
 편집기 코드 창은 <xref:Microsoft.VisualStudio.Shell.WindowPane> 새 WPF 인터페이스 뿐만 아니라 이전 Win32 인터페이스를 구현 하는에서 파생 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> . 메서드를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> HWND 기반 호스팅 환경을 만들거나 메서드를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> WPF 호스팅 환경을 만들 수 있습니다. 기본 편집기는 항상 WPF를 사용 하지만 사용자 고유의 내용에이 창 창을 직접 포함 하는 경우 호스팅 요구 사항에 적합 한 창 종류를 만들 수 있습니다.  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>Win32 및 WPF 버전의 IVsTextView 사용  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>을 Win32 모드나 WPF 모드로 설정할 수 있습니다.  
  
 편집기 팩터리가 텍스트 뷰를 만드는 경우 기본적으로 HWND 내에서 호스트 되 고 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> hwnd를 반환 합니다. WPF 컨트롤 내에 편집기를 포함 하려면이 모드를 사용 하면 안 됩니다.  
  
 텍스트 뷰를 WPF 모드로 설정 하려면를 호출 하 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> 고 <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> 매개 변수에서 초기화 플래그 중 하나로 전달 해야 합니다 `InitView` . 을 호출 하 여을 가져올 수 있습니다 <xref:System.Windows.FrameworkElement> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A> .  
  
 WPF 모드는 두 가지 방법으로 Win32 모드와 다릅니다. 먼저, 텍스트 뷰를 WPF 컨텍스트에서 호스트할 수 있습니다. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>을로 캐스팅 하 고를 호출 하 여 WPF 창에 액세스할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A> . 둘째,는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> 여전히 hwnd를 반환 하지만이 hwnd는 해당 위치를 확인 하 고 포커스를 설정 하는 데만 사용할 수 있습니다. 편집기에서 창을 그리는 방법에 영향을 주지 않으므로 WM_PAINT 메시지에 응답 하는 데이 HWND를 사용 하지 않아야 합니다. 이 HWND는 어댑터를 통해 새 편집기 코드로의 전환을 용이 하 게 하는 데만 제공 됩니다. `VIF_NO_HWND_SUPPORT`이 모드에서 반환 되는 hwnd의 제한 때문에 구성 요소에서 hwnd가 작동 해야 하는 경우에는를 사용 하지 않는 것이 좋습니다 `GetWindowHandle` .  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>네이티브 코드에서 배열을 매개 변수로 전달  
 레거시 편집기 API에는 배열 및 개수를 포함 하는 매개 변수가 있는 여러 메서드가 있습니다. 예:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 네이티브 코드에서 이러한 메서드를 호출 하는 경우 한 번에 하나의 요소만 전달 해야 합니다. 둘 이상의 요소를 전달 하는 경우 주 interop 구현 문제로 인해 호출이 거부 됩니다.  
  
 이 문제는와 같은 메서드를 사용 하 여 더 복잡 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A> . 이 메서드는 호출 될 때마다 무시 된 마커 형식의 이전 목록을 지우므로,이 메서드는 세 가지 표식 유형을 사용 하 여 세 번 호출 하는 것만 가능 합니다. 유일한 해결책은 관리 코드 에서만이 메서드를 호출 하는 것입니다.  
  
#### <a name="threading"></a>스레딩  
 항상 UI 스레드에서 버퍼 어댑터를 호출 해야 합니다. 버퍼 어댑터는 관리 되는 개체입니다. 즉, 관리 되는 코드에서이 개체를 호출 하면 COM 마샬링이 무시 되 고 호출은 UI 스레드로 자동으로 마샬링되지 않습니다.  백그라운드 스레드에서 버퍼 어댑터를 호출 하는 경우 또는 비슷한 메서드를 사용 해야 합니다 <xref:System.Windows.Threading.Dispatcher.Invoke%2A> .  
  
#### <a name="lockbuffer-methods"></a>LockBuffer 메서드  
 모든 LockBuffer () 메서드는 더 이상 사용 되지 않습니다. 예:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>커밋 이벤트  
 커밋 이벤트는 지원 되지 않습니다. 이러한 이벤트에 대해 권장 하는 메서드를 호출 하면 메서드가 오류 코드를 반환 합니다.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 가 <xref:EnvDTE.TextEditorEvents> Commit ()에서 더 이상 발생 하지 않습니다. 대신 모든 텍스트 변경을 발생 시킵니다.  
  
#### <a name="text-markers"></a>텍스트 표식  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A>개체를 제거할 때 개체에 대해를 호출 해야 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> . 이전 버전에서는 표식을 릴리스 하기만 하면 됩니다.  
  
#### <a name="line-numbers"></a>줄 번호  
 및의 다양 한 메서드에 대 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 한 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx> 줄 번호는 Visual Studio 2008에서와 같이 개요 및 자동 줄 바꿈의 영향을 받지 않는 줄 번호가 아니라 기본 버퍼 줄 번호에 해당 합니다.  
  
 영향을 받는 방법에는 다음이 포함 됩니다 (목록은 완전 하지 않음).  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### <a name="outlining"></a>개요  
 의 클라이언트는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 또는을 사용 하 여 추가 된 개요 영역만 볼 수 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A> 있습니다. 편집기 어댑터를 통해 추가 되지 않기 때문에 임시 지역이 표시 되지 않습니다. 마찬가지로 이러한 클라이언트는 편집기 어댑터 대신 새 편집기 코드를 사용 하는 언어 (c # 및 c + + 포함)에서 추가 된 개요 영역을 볼 수 없습니다.  
  
#### <a name="line-heights"></a>줄 높이  
 새 편집기에서 텍스트 줄의 높이는 다른 줄을 기준으로 줄을 이동할 수 있는 글꼴 크기와 가능한 줄 변환에 따라 서로 다를 수 있습니다. 과 같은 메서드에서 반환 되는 줄 높이는 줄 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> 변환이 적용 되지 않은 기본 글꼴 크기를 사용 하는 선의 높이입니다. 이 높이는 뷰에서 선의 실제 높이가 반영 될 수도 있고 그렇지 않을 수도 있습니다.  
  
#### <a name="eventing-and-undo"></a>이벤트 및 실행 취소  
 새 편집기에서 뷰는 실행 취소 클러스터가 열린 경우에도 계속 해 서 이벤트를 렌더링 하 고 발생 시키는 등의 작업을 계속 수행 합니다. 이 동작은 실행 취소 클러스터를 닫을 때까지 이러한 작업을 수행 하지 않은 레거시 보기와는 다릅니다.  
  
#### <a name="intellisense"></a>IntelliSense  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A>또는 중 하나를 구현 하지 않는 클래스를 전달 하면 메서드가 실패 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3> . 사용자 지정 Win32 소유자가 그린 팝업은 더 이상 지원 되지 않습니다.  
  
#### <a name="smarttags"></a>창이  
 ,, 및 인터페이스를 사용 하 여 만든 스마트 태그에 대해서는 어댑터를 지원 하지 않습니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> .  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch> 가 구현 되지 않았습니다.  
  
## <a name="unimplemented-methods"></a>구현 되지 않은 메서드  
 일부 메서드는 텍스트 버퍼 어댑터, 텍스트 뷰 어댑터 및 텍스트 계층 어댑터에서 구현 되지 않았습니다.  
  
|인터페이스|구현되지 않음|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` 가 구현 되지 않았습니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> 는 어댑터에서 구현 되지만 개요 UI는 무시 됩니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> 는 어댑터에서 구현 되지만 개요 UI는 무시 됩니다.|

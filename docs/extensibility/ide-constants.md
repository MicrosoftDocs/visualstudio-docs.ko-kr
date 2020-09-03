---
title: IDE 상수 | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc2eddac1cc7d7e616deb197752adf41a4d68d15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710498"
---
# <a name="ide-constants"></a>IDE 상수

<xref:Microsoft.VisualStudio.VSConstants>클래스는 IDE (통합 개발 환경)와 관련 된 상수를 제공 하며, 이전에는 헤더 파일에만 정의 되었습니다.

## <a name="logical-and-physical-views"></a>논리적 및 물리적 뷰

|값|설명|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`처리기는이 값을 메서드에 전달 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 하 여 **연결 프로그램** 대화 상자를 가져와야 합니다 .이 경우에는 가능한 코드 뷰를 사용 해야 합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`처리기는이 값을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 메서드에 전달 하 여 **연결 프로그램** 대화 상자를 가져옵니다 .이 경우는 <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> 와 동일한 뷰로 매핑되는 가능한 디버깅 뷰로 채워집니다 <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid> .|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`처리기는이 값을 메서드에 전달 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> **연결 프로그램** 대화 상자를 가져옵니다 .이 경우 폼 디자이너 뷰를 **볼** 수 있습니다.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`처리기는이 값을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 메서드에 전달 하 여 **연결 프로그램** 대화 상자를 가져옵니다 .이 경우 편집기 팩터리의 기본/기본 뷰입니다.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`처리기는이 값을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 메서드에 전달 하 여 **연결 프로그램** 대화 상자를 가져옵니다 .이 대화 상자에는 문서 또는 데이터 텍스트 편집기 뷰가 있습니다.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`처리기는이 값을 메서드에 전달 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 사용자가 사용할 사용자 정의 뷰를 선택 하 라는 메시지를 표시 합니다.|

## <a name="editor-factory-flags"></a>편집기 팩터리 플래그

|값|설명|
|-----------|-----------------|
|[CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|메서드의 첫 번째 매개 변수로 비트를 결합 한 사용 되지 않는 플래그 <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> 입니다.|
|[CEF. OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|비트를, 메서드의 첫 번째 매개 변수로 결합 하면 <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> 편집기 팩터리가 필요한 수정을 수행 해야 함을 나타냅니다.|
|[CEF. System.windows.forms.openfiledialog.openfile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|비트를 메서드의 첫 번째 매개 변수로 결합 <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> 한이 플래그는 Cef와 함께 사용할 수 없습니다 [. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[CEF. 무음](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|메서드의 첫 번째 매개 변수로 비트를 결합 <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> 한 것은 편집기 팩터리가 UI (사용자 인터페이스)를 표시 하지 않고 편집기를 만들어야 함을 나타냅니다.|

## <a name="visual-studio-errors"></a>Visual Studio 오류

|값|설명|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|해당 개체가 이미 사용 중인 경우의 비동기 동작에 대 한 인터페이스에서 반환 되는 상수입니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|"호환 되지 않는 문서 데이터"에 대 한 Visual Studio와 관련 된 오류 HRESULT입니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Visual Studio와 관련 된 오류 HRESULT 이며 "패키지가 로드 되지 않았습니다."를 나타냅니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Visual Studio와 관련 된 오류 HRESULT 이며 "프로젝트가 이미 있습니다."를 나타냅니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Visual Studio와 관련 된 오류 HRESULT 이며 "프로젝트 구성에 실패 했습니다."를 나타냅니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Visual Studio와 관련 된 오류 HRESULT 이며, "프로젝트가 로드 되지 않았습니다."를 나타냅니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Visual Studio와 관련 된 오류 HRESULT 이며 "솔루션이 이미 열려 있습니다."를 나타냅니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Visual Studio와 관련 된 오류 HRESULT 이며 "솔루션이 열려 있지 않습니다."를 나타냅니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|인터페이스에서 배열을 지정 하는 매개 변수를 포함 하는 빌드 인터페이스에서 반환 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> 되지만 구현에서는 모든 출력에만 메서드를 적용할 수 있습니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>문서에 편집기에서 열 수 없는 형식이 있는 경우 메서드는이 값을 반환 합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|사용자가 Visual Studio 마법사의 뒤로 단추를 누르면 표시 되는 HRESULT 값입니다.|

## <a name="visual-studio-constants"></a>Visual Studio 상수

|값|설명|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Visual Studio와 관련 된 오류 HRESULT 이며 "프로젝트 전달 됨"을 나타냅니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Visual Studio와 관련 된 "도구 상자 마커"에 해당 하는 상수입니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|모달 시작을 나타내는 메서드를 통해 알림 메시지를 브로드캐스팅하는 데 사용할 수 있는 Visual Studio 관련 상수입니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> .|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A>모달 형식의 끝을 나타내는 메서드를 통해 알림 메시지를 브로드캐스팅하는 데 사용할 수 있는 Visual Studio 관련 상수입니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A>명령 모음 메트릭이 변경 되었음을 나타내는 메서드를 통해 알림 메시지를 브로드캐스팅 하기 위한 Visual Studio 관련 상수입니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|쿠키가 설정 되지 않았음을 나타내는 Visual Studio 관련 상수입니다.|
|[VSITEMID. 인지](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|프로젝트 항목이 없다는 것을 나타내는 Visual Studio 항목 식별자입니다. 이 값은 현재 선택 영역이 없는 경우에 사용 됩니다.|
|[VSITEMID. 루트가](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|단일 항목이 아닌 전체 계층 구조를 식별 하는 데 사용 되는 프로젝트 계층 구조의 루트를 나타내는 Visual Studio 항목 식별자입니다.|
|[VSITEMID. 선택](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|계층의 루트를 포함할 수 있는 현재 선택 된 항목을 나타내는 Visual Studio 항목 식별자입니다.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 호출에서 선택한 IDE의 구성 요소를 설명 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> 합니다 (예:).

|상수|값|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement. StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement. 관리자 관리자](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement. UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement. WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 새 선택 상태를 나타내는 데 사용 되는 상수입니다.

|상수|값|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|

## <a name="component-selector-dialog-constants"></a>구성 요소 선택기 대화 상자 상수

|상수|값|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER + 1280|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER + 1281|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER + 1290|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER + 1287|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER + 1285|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER + 1288|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER + 1286|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER + 1289|

## <a name="see-also"></a>추가 정보

- [프로젝트 시스템 확장을 위한 IDE 정의 명령](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

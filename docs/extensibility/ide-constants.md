---
title: IDE 상수 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710498"
---
# <a name="ide-constants"></a>IDE 상수

클래스는 <xref:Microsoft.VisualStudio.VSConstants> 통합 개발 환경(IDE)에 특정하고 이전에 헤더 파일에서만 정의된 상수를 제공합니다.

## <a name="logical-and-physical-views"></a>논리적 및 물리적 보기

|값|Description|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` 처리기는 가능한 코드 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 뷰에서 이 값을 메서드에 전달하여 대화 상자 **열기를** 얻어야 합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` 처리기는 이 값을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 메서드에 전달하여 대화 상자 **열기를** 얻을 수 <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> 있으며, 이 경우 <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>동일한 뷰에 매핑되는 디버깅 뷰가 채워집니다.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` 처리기는 이 값을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 메서드에 전달하여 **[With 열기]** 대화 상자를 얻을 수 있으며, 이 경우 양식 디자이너 보기 **보기로 이동합니다.**|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` 처리기는 이 값을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 메서드에 전달하여 **With 열기** 대화 상자를 가져옵니다.이 경우 편집기 팩터의 기본/기본 보기입니다.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` 처리기는 이 값을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 메서드에 전달하여 문서 또는 데이터 텍스트 편집기 보기에 대해 **With 열기** 대화 상자를 가져옵니다.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` 처리기는 이 값을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 메서드에 전달하여 사용할 사용자 정의 보기를 선택하라는 메시지를 표시합니다.|

## <a name="editor-factory-flags"></a>에디터 팩토리 플래그

|값|Description|
|-----------|-----------------|
|[Cef. 복제파일](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> 메서드의 첫 번째 매개 변수로 비트씩 결합된 더 이상 사용되지 않는 플래그입니다.|
|[Cef. 오픈아스뉴](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>을 의 첫 번째 매개 변수로 비트로 결합하면 편집기 팩터리는 필요한 수정을 수행해야 합니다.|
|[Cef. Openfile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> 메서드의 첫 번째 매개 변수로 비트씩 결합된 이 플래그는 [CEF를 상호 배타적입니다. 복제파일](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[Cef. 침묵](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> 메서드의 첫 번째 매개 변수로 비트씩 결합하면 편집기 팩터리는 사용자 인터페이스(UI)를 표시하지 않고 편집기 팩터링을 만들어야 한다는 것을 나타냅니다.|

## <a name="visual-studio-errors"></a>비주얼 스튜디오 오류

|값|Description|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|문제의 개체가 이미 사용 중일 때 비동기 동작에 대한 인터페이스에서 반환되는 상수|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|"호환되지 않는 문서 데이터"에 대한 Visual Studio와 관련된 오류 HRESULT입니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Visual Studio에 만적용되는 오류 HRESULT이며 "패키지가 로드되지 않음"을 나타냅니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Visual Studio에 만연하고 "프로젝트가 이미 존재"를 나타내는 오류 HRESULT입니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Visual Studio에 만적용되는 오류 HRESULT이며 "프로젝트 구성실패"를 나타냅니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Visual Studio에 만적용되는 오류 HRESULT이며 "프로젝트가 로드되지 않음"을 나타냅니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Visual Studio에 만연하고 "솔루션이 이미 열려 있는 솔루션"을 나타내는 오류 HRESULT입니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Visual Studio에 만연하고 "솔루션이 열리지 않음"을 나타내는 오류 HRESULT입니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> 인터페이스에서 배열을 지정하기 위한 매개 변수가 있는 빌드 인터페이스에서 반환되지만 구현은 메서드를 모든 출력에만 적용할 수 있습니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|문서에 <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> 편집기에서 열 수 없는 형식이 있는 경우 메서드는 이 값을 반환합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|사용자가 Visual Studio 마법사에서 뒤로 단추를 눌렸음을 나타내는 HRESULT 값입니다.|

## <a name="visual-studio-constants"></a>비주얼 스튜디오 상수

|값|Description|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Visual Studio에 만적용되는 오류 HRESULT이며 "프로젝트 전달"을 나타냅니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|"도구 상자 마커"에 대한 Visual Studio에만 적용되는 상수입니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|양식의 시작을 나타내는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> 메서드를 통해 알림 메시지를 브로드캐스트하기 위한 Visual Studio에만 적용되는 상수입니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|양식의 끝을 나타내는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> 메서드를 통해 알림 메시지를 브로드캐스트하기 위한 Visual Studio에만 적용되는 상수입니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|명령 모음 메트릭이 변경되었음을 나타내는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> 메서드를 통해 알림 메시지를 브로드캐스트하기 위한 Visual Studio에만 적용되는 상수입니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|쿠키가 설정되지 되었음을 나타내는 Visual Studio에만 적용되는 상수입니다.|
|[VSITEMID. 없음](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|프로젝트 항목의 부재를 나타내는 Visual Studio 항목 식별자입니다. 이 값은 현재 선택 영역이 없을 때 사용됩니다.|
|[VSITEMID. 루트](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|프로젝트 계층구조의 루트를 나타내고 단일 항목이 아닌 전체 계층을 식별하는 데 사용되는 Visual Studio 항목 식별자입니다.|
|[VSITEMID. 선택](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|계층의 루트를 포함할 수 있는 현재 선택된 항목 또는 항목을 나타내는 Visual Studio 항목 식별자입니다.|

## <a name="ivsselectionevents"></a>아이브셀렉션이벤트
 예를 들어 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> 호출에서 방금 선택한 IDE의 구성 요소에 대해 설명합니다.

|상수|값|
|--------------|-----------|
|[선택요소.문서프레임](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[선택요소.속성 브라우저SID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[선택요소.스타트업 프로젝트](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[선택요소.관리자](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[선택요소.사용자 컨텍스트](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[선택요소.창프레임](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VS셀레미드
 새 선택 상태를 나타내는 데 사용되는 상수입니다.

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

## <a name="see-also"></a>참조

- [프로젝트 시스템 확장을 위한 IDE 정의 명령](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

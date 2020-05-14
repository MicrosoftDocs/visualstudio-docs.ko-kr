---
title: 이용 가능한 서비스 목록 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, Visual Studio
- Visual Studio, services
ms.assetid: 724eb24b-b87c-4971-a2e7-adee7afc03b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 302d4bcff647a74acc973c47e0b62e66c86e5859
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707338"
---
# <a name="list-of-available-services"></a>사용 가능한 서비스 목록

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]및 비주얼 스튜디오 SDK는 다음과 같은 서비스를 지원합니다. 일부 패키지는 여기에 나열되지 않은 자체 서비스를 제공합니다(예: 언어 서비스에는 단일 서비스 GUID가 없습니다). 레지스트리에서 언어 서비스의 GUID를 찾으려면 언어 이름을 사용해야 합니다.

여기에 나열되거나 다른 소스(예: 언어 서비스)에서 얻은 서비스 GUID를 사용하여 각 서비스에 표시된 기본 인터페이스 또는 인터페이스를 가져옵니다.

## <a name="the-services"></a>서비스

| 서비스 | 인터페이스 | Visual Studio | Visual Studio 2005 | 설명 |
| - | - |---------------|--------------------| - |
| <xref:Microsoft.VisualStudio.OLE.Interop.SBindHost> | <xref:Microsoft.VisualStudio.OLE.Interop.IBindHost> | 예 | 예 | VSPackage에서 ActiveX 컨트롤에서 <xref:Microsoft.VisualStudio.OLE.Interop.IBindHost> 인터페이스를 가져와 비동기 데이터 전송을 용이하게 하는 데 사용합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SDTE> | <xref:EnvDTE.DTE> | 예 | 예 | 자동화에 사용되는 설계 시간 확장성(DTE) 개체를 가져옵니다.<br /><br /> C/C++ ID: SID_SDTE |
| <xref:Microsoft.VisualStudio.Shell.Interop.SCodeNavigate> | <xref:Microsoft.VisualStudio.Shell.Interop.ICodeNavigate> | 예 | 예 | 컨트롤에 대 한 기본 이벤트 처리기를 표시 하는 폼 디자이너에 의해 구현 됩니다. |
| <xref:Microsoft.VisualStudio.OLE.Interop.SContainerDispatch> | IDispatch | 예 | 예 | VSPackage가 다른 VSPackage 또는 컨트롤의 자동화 인터페이스에 액세스할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SExtendedTypeLib> | <xref:Microsoft.VisualStudio.Shell.Interop.IExtendedTypeLib> | 예 | 예 | VSPackage가 확장 형식 라이브러리를 추가하거나 만들 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SDirList> | <xref:Microsoft.VisualStudio.Shell.Interop.IDirList> | 예 | 예 | 컨테이너의 명명된 목록 목록에 대한 액세스를 제공합니다. 예를 들어 검색할 디렉터리 목록과 찾기 **및 바꾸기** 대화 상자에서 검색할 수 있습니다. **Look In** 개체는 <xref:Microsoft.VisualStudio.Shell.Interop.IDirList> 기록뿐만 아니라 읽을 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SIVsPackageDynamicToolOwner> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwner> | 예 | 예 | VSPackage에 자체 도구 창이 동적으로 표시또는 숨김을 갖도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SLicensedClassManager> | <xref:Microsoft.VisualStudio.Shell.Interop.ILicensedClassManager> | 예 | 예 | VSPackage가 라이센스 키 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 목록을 지정하여 필요한 클래스를 나타낼 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> | <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> | 예 | 예 | VSPackage가 로컬 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 레지스트리 하이브를 기준으로 레지스트리에 액세스할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.OLE.Interop.SOleComponentManager> | <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager> | 예 | 예 | 메시지 루프, 키보드 루프 및 이벤트 알림과 같은 구성 요소 조정 서비스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> | 예 | 예 | VSPackage가 도움말, 상태 표시줄 및 UI [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]이벤트와 같은 다양한 UI(사용자 인터페이스) 요소에 액세스할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SOleInPlaceComponent> | <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> | 예 | 예 | VSPackage가 해당 UI를 의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]UI와 통합할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SOleInPlaceComponentSite> | <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentSite> | 예 | 예 | VSPackage에서 도구와 관련된 UI 변경 내용을 제어할 수 있습니다. |
| <xref:Microsoft.VisualStudio.OLE.Interop.SOleUndoManager> | <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> | 예 | 예 | VSPackage가 컨테이너의 취소 관리자에 액세스하여 해당 컨테이너의 취소 스택에 참여하거나 해당 컨테이너의 취소 스택에 액세스할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService> | <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> | 예 | 예 | VSPackage가 자체 서비스를 제공할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SProfferTypeLib> | <xref:Microsoft.VisualStudio.Shell.Interop.IProfferTypeLib> | 예 | 예 | 양식 디자이너를 사용하여 형식 라이브러리를 참조할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> | <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> | 예 | 예 | 선택 컨테이너의 선택 항목에 대한 액세스를 제공합니다. 양식 디자이너가 사용합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SUIHostCommandDispatcher> | <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> | 예 | 예 | VSPackage가 명령 처리기 체인에 참여하고 통합 개발 환경(IDE) 또는 그 자체를 대신하여 명령을 처리할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SUIHostLocale> | <xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale> | 예 | 예 | 호스트의 UI 로캘 정보에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> | 예 | 예 | 로깅이 켜져 있을 때 VSPackage에서 상위 수준 메시지를 기록할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddProjectItemDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg> | 예 | 예 | VSPackage가 자체 **항목 추가** 메뉴 옵션을 구현할 수 있도록 프로젝트 **항목 추가** 대화 상자에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg> | 예 | 예 | 참조 **추가** 대화 상자를 표시합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> | 예 | 예 | VSPackage를 사용하여 명령줄 스위치가 devenv.exe에 제공되었는지 여부를 확인할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCallBrowser> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCallBrowser> | 예 | 예 | VSPackage가 디버깅에 사용되는 새 **호출 브라우저를** 만들 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsClassView> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsClassView> | 예 | 예 | VSPackage가 **클래스 뷰를** 특정 개체에 동기화할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCmdNameMapping> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCmdNameMapping> | 예 | 예 | GUID 및 뒤로 명령 이름을 매핑하고 사용 가능한 모든 명령 및 이름의 이름을 결정하는 데 대한 지원을 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCodeDefView> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCodeDefView> | 예 | 예 | VSPackage에서 코드 정의 **보기를**조작할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCodeShareHandler> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCodeShareHandler> | 예 | 예 | 내부 서비스. 사용하지 마십시오. |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsCodeWindow> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> | 예 | 예 | 하나 이상의 문서를 포함할 수 있는 코드 창에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsCodeWindowManager> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> | 예 | 예 | VSPackage에서 드롭다운 막대와 같은 코드 창에 변경 내용을 추가할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCommandWindow> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindow><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindow2> | 예 | 예 | VSPackage명령 **창을** 통해 명령을 실행하고 그렇지 않으면 **명령 창과**상호 작용할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCommandWindowsCollection> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindowsCollection> | 예 | 예 | VSPackage에서 유지 관리하는 **명령** 창 목록을 조작할 수 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsComplusLibrary> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibraryReferenceManager> | 예 | 예 | VSPackage가 **개체 브라우저에**찾아보기 정보를 제공할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsComponentSelectorDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsComponentSelectorDlg> | 예 | 예 | VSPackage가 **참조 추가** 옵션을 지원하도록 하여 사용자가 프로젝트에 추가할 외부 구성 요소를 선택할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsComponentSelectorDlg2> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsComponentSelectorDlg2> | 예 | 예 | VSPackage가 **참조 추가** 옵션을 지원하도록 하여 사용자가 프로젝트에 추가할 외부 구성 요소를 선택할 수 있도록 합니다. 이 버전의 대화 상자를 사용하면 구성 요소 목록이 표시되기 전에 미리 채울 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsConfigurationManagerDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsConfigurationManagerDlg> | 예 | 예 | 구성 **관리자** 대화 상자가 표시됩니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject> | 예 | 예 | VSPackage가 다른 프로젝트의 컬렉션을 포함하는 프로젝트를 만들 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsDebuggableProtocol> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProtocol> | 예 | 예 | VSPackage를 사용하여 IDE에서 특정 디버그 엔진을 시작하는 데 사용하는 디버깅 가능한 프로토콜 목록을 업데이트할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsDebugLaunch> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugLaunch> | 예 | 예 | VSPackage가 디버거 시작을 지원할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsDiscoveryService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService> | 예 | 예 | VSPackage가 웹 서비스를 검색하는 데 사용되는 검색 세션을 만들 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsEnumHierarchyItemsFactory> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumHierarchyItemsFactory> | 예 | 예 | 지정된 계층(프로젝트)을 통해 열거하는 데 사용되는 개체를 만드는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumHierarchyItemsFactory> 팩터리를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsErrorList> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsErrorList> | 예 | 예 | **빌드 오류 목록** 작업 창을 조작하기 위한 추가 메서드를 제공합니다. 특히 빌드 **오류 목록** 작업 창을 최전선에 가져오고 모든 오류를 표시하도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager> | 예 | 예 | 현재 솔루션의 **기타 파일** 프로젝트 노드에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChange> | | 예 | 예 | 더 이상 사용되지 않습니다. 대신 `SVsFileChangeEx` 서비스를 사용합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> | 예 | 예 | VSPackage가 IDE에 의해 트리거되는 다양한 파일 변경 이벤트에 액세스할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFilterAddProjectItemDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> | 예 | 예 | VSPackage가 **항목 추가** 대화 상자에 나타나는 항목을 필터링할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFilterKeys> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterKeys> | 예 | 예 | VSPackage에서 고급 키보드 필터링을 수행할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFontAndColorCacheManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> | 예 | 예 | 글꼴 및 색상에 대한 캐시 집합에 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 대한 액세스를 제공하여 특정 캐시 또는 모든 캐시를 새로 고치거나 지웁히 지웁습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFontAndColorStorage> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities> | 예 | 예 | VSPackage에서 유지 관리하는 글꼴 및 색상 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]설정을 조작할 수 있습니다. 또한 이 서비스는 글꼴 및 색상 데이터를 조작하기 위한 유틸리티 메서드 컬렉션에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> | 예 | 예 | 필요에 따라 만드는 일반 **출력 창에** 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsHelpService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsHelpSystem> | 예 | 예 | 도움말 시스템에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsHTMLConverter> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsHTMLConverter> | 예 | 예 | HTML을 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 처리하여 출력을 포맷하는 데 디버거에서 사용됩니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIME> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsIME> | 예 | 예 | VSPackage 내에서 IME(입력 메서드 편집기) API에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIntegratedHelp> | <xref:Microsoft.VisualStudio.VSHelp.SVsHelp> | 예 | 예 | 도움말 파일을 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 통해 키워드 또는 URL 액세스에 대한 도움말 시스템에 대한 액세스와 탐색 제어를 제공합니다. 이 서비스는 도움말이 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE에 통합되어 있고 외부 프로그램으로 실행되지 않는 경우에만 사용할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIntelliMouseHandler> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntelliMouseHandler> | 예 | 예 | VSPackage가 마우스 휠을 사용하고 마우스 휠을 클릭할 때 스크롤 및 팬 비트맵 처리와 같은 IntelliMouse 기능에 액세스할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseEngine> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseEngine> | 예 | 예 | 프로젝트 계층 노드가 IntelliSense 작업에 대한 지원의 일부로 파일을 로드하거나 언로드할 수 있도록 합니다. 로드 및 언로드 프로세스는 프로젝트에 대한 IntelliSense 도구 설명에 표시되는 내용에 영향을 줄 수 있는 이벤트를 트리거합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseProjectHost> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProjectHost> | 예 | 예 | 프로젝트 계층 노드가 IntelliSense 도구 설명에 표시할 <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> 수 있는 중첩된 IntelliSense 프로젝트(인터페이스를 구현하는)에 대한 정보를 제공할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseProjectManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProjectManager> | 예 | 예 | 프로젝트 계층 노드가 IntelliSense 도구 설명에 표시되는 내용에 영향을 줄 수 있는 참조 또는 구성 변경과 같은 이벤트의 리스너에게 조언할 수 있도록 합니다. 포함된 언어와 함께 사용할 수 있도록 설계되었습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsInvisibleEditorManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> | 예 | 예 | VSPackage가 완전한 편집 기능을 제공하지만 사용자에게 표시되지 않는 "보이지 않는" 편집기, 즉 편집기를 등록할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsLanguageFilter> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> | 예 | 예 | VSPackage가 데이터 팁 및 단어 의 범위와 같은 텍스트 보기에 추가 정보를 제공할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsLaunchPad> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPad> | 예 | 예 | VSPackage가 임시 일괄 처리 스크립트를 실행하고, 출력창으로 출력이 전송되는 명령줄 프로그램을 실행하고, 오류 창으로 전송되는 표준 경고 및 오류 메시지를 구문 분석할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsLaunchPadFactory> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPadFactory> | 예 | 예 | 개체를 만들기 <xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPad> 위한 팩터리를 제공합니다. |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsLinkedUndoTransactionManager> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> | 예 | 예 | 연결된 취소 관리자에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsMenuEditor> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsMenuEditorFactory> | 예 | 예 | 양식 디자이너가 공유 메뉴 편집기에 액세스할 수 있도록 합니다. IVsMenuEditor팩토리에 대해 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMenuEditor>쿼리할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> | 예 | 예 | VSPackage가 특정 컨텍스트에 대한 도움말 키워드를 연결하는 데 사용되는 "컨텍스트 백"을 만들 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjBrowser> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjBrowser> | 예 | 예 | VSPackage개체 **브라우저의**특정 개체로 이동할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager> | 예 | 예 | VSPackage가 네임스페이스, 클래스 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 및 열거체와 같은 개체를 관리하기 위해 라이브러리 관리자를 등록할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectSearch> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectSearch> | 예 | 예 | VSPackage가 특정 개체를 검색할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsOpenProjectOrSolutionDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsOpenProjectOrSolutionDlg> | 예 | 예 | VSPackage가 표준 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 대화 상자를 사용하여 프로젝트 또는 솔루션을 열 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> | 예 | 예 | VSPackage가 일반 출력 창에서 추가 출력 창을 만들 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsParseCommandLine> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsParseCommandLine> | 예 | 예 | <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스 구현자가 명령줄을 구문 분석할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsPathVariableResolver> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsPathVariableResolver> | 예 | 예 | 경로에 포함된 변수를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 해결하여 최종 경로를 생성하는 방법을 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsPreviewChangesService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsPreviewChangesService> | 예 | 예 | 리팩터링 코드에 사용되는 **변경 내용 미리 보기** 대화 상자를 표시합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsProfileDataManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsProfileDataManager> | 예 | 예 | 설정 데이터를 가져오고 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 내보낼 뿐만 아니라 현재 사용자의 프로필 설정의 UI를 표시할 수 있는 프로필 관리자에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsProfilesManagerUI> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsProfilesManagerUI> | 예 | 예 | 현재 사용자의 프로필 설정을 보여주는 대화 상자를 표시합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsPropertyPageFrame> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPageFrame> | 예 | 예 | VSPackage가 **속성** 창에 처음에 표시되는 속성 페이지를 재정의할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | 예 | 예 | VSPackages에서 파일을 메모리에서 변경하거나 저장하려고 한다는 것을 소스 제어 공급자에게 알리는 데 사용됩니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterDebugTargetProvider> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectDebugTargetProvider> | 예 | 예 | VSPackage 프로젝트를 사용하여 디버거에서 시작할 대상을 프로그래밍 방식으로 재정의할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors> | 예 | 예 | VSPackage가 IDE에 편집기 팩터리를 등록할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsRegisterFindScope> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsRegisterFindScope> | 예 | 예 | VSPackage에서 **파일 찾기** 대화 상자에 대한 검색 범위를 등록할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterPriorityCommandTarget> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget> | 예 | 예 | VSPackage를 우선 순위가 높은 명령 처리기로 등록할 수 있도록 하여 VSPackage에서 모든 명령을 볼 수 있습니다. 아껴서 사용하십시오. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes> | 예 | 예 | VSPackage가 IDE에 프로젝트 유형을 등록할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsResourceManager> | 예 | 예 | VSPackage가 위성 DLL에서 관리되고 관리되지 않는 리소스를 로드할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceView> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsResourceView> | 예 | 예 | 대신 <xref:Microsoft.VisualStudio.Shell.Interop.SVsClassView> 서비스를 사용합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> | 예 | 예 | 현재 열려 있는 모든 문서를 추적하는 IDE의 실행 중인 문서 테이블(RDT)에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | 예 | 예 | VSPackage가 소스 제어 공급자에 자신을 등록하여 소스 제어에 참여할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccToolsOptions> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | 예 | 예 | VSPackage에서 소스 제어 공급자 옵션을 얻고 설정할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSettingsReader> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> | 예 | 예 | 사용자의 프로필 설정에 대한 읽기 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell> | 예 | 예 | VSPackage가 다른 VSPackage와 직접 상호 작용하고 조작할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger> | 예 | 예 | [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버거에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> | 예 | 예 | VSPackage가 현재 선택 영역에 액세스하고 명령 UI 컨텍스트를 관리할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVSMDCodeDomProvider> | IVSMD코드돔제공자 | 예 | 예 | 네이티브 코드에서 사용할 수 있는 DOM(코드 문서 개체 모델) 공급자에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVSMDDesignerService> | IVSMD코드돔크리에이터<br /><br /> IVSMD디자이너서비스 | 예 | 예 | 관리되는 양식 디자이너에 대한 IDE 지원에 대한 액세스를 제공합니다. 는 `IVSMDCodeDomCreator` 코드 DOM 공급자를 만드는 데 사용할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVSMDPropertyBrowser> | IVSMD프로퍼티브라우저 | 예 | 예 | 디자이너 속성 창 서비스에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVSMDTypeResolutionService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVSMDTypeResolutionService> | 예 | 예 | 네이티브 코드에서 사용할 수 <xref:System.ComponentModel.Design.ITypeResolutionService> 있는 개체를 반환할 수 있는 인터페이스에 대 한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSmartOpenScope> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSmartOpenScope> | 예 | 예 | 필요에 따라 잠금을 고려하여 어셈블리에서 범위를 여는 방법을 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> | 예 | 예 | 현재 솔루션에 대한 최상위 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager> | 예 | 예 | VSPackage가 솔루션의 빌드 프로세스와 상호 작용할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionObject> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> | 예 | 예 | 대신 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> 서비스를 사용합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionPersistence> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> | 예 | 예 | VSPackage가 현재 솔루션의 .sln 파일에서 정보를 저장하고 검색할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSQLCLRReferences> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSQLCLRReferences> | 예 | 예 | 관리되는 코드 어셈블리에서 참조를 추가하고 업데이트하는 기능을 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsStartPageDownload> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsStartPageDownload> | 예 | 예 | 백그라운드 스레드에서 다운로드 서비스를 시작하고 중지하기 위한 Visual Studio 2017 Start Page의 다운로드 서비스에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> | 예 | 예 | IDE의 상태 표시줄에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsStrongNameKeys> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsStrongNameKeys> | 예 | 예 | 관리되는 코드 어셈블리에 서명하는 데 사용되는 암호를 사용하여 강력한 키 이름 및 키 파일을 만드는 메서드에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsStructuredFileIO> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsStructuredFileIO> | 예 | 예 | VSPackage가 여러 형식으로 데이터를 저장하는 지원을 제공할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> | 예 | 예 | IDE의 작업 목록 창에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextImageUtilities> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextImageUtilities> | 예 | 예 | 텍스트 파일을 로드하고 저장하는 유틸리티를 제공합니다. |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> | 예 | 예 | IDE에서 사용할 수 있는 숨겨진 영역의 숨겨진 텍스트 세션뿐만 아니라 모든 텍스트 버퍼에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsTextOut> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsTextOut> | 예 | 예 | 장치 컨텍스트에 텍스트를 쓰기 `TextOut` 위한 Win32 함수 버전을 제공합니다(DC 핸들 필요). |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextSpanSet> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextSpanSet> | 예 | 예 | 텍스트 이미지 또는 버퍼의 텍스트 범위 목록에 대한 액세스를 제공합니다. 이 서비스는 일반적으로 문서 컨테이너에서 구현되며 현재 문서를 참조합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsThreadedWaitDialog> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsThreadedWaitDialog> | 예 | 예 | VSPackage가 백그라운드 작업을 기다리는 데 사용되는 다른 스레드에서 대기하는 대화 상자를 표시할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsThreadPool> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsThreadPool> | 예 | 예 | VSPackage에서 유지 관리되는 백그라운드 작업을 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]시작할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox> | 예 | 예 | IDE의 **도구 상자에**대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolboxActiveXDataProvider> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider> | 예 | 예 | VSPackage가 **도구 상자** 항목에서 정보를 가져올 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolboxDataProviderRegistry> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProviderRegistry> | 예 | 예 | VSPackage가 **전체**도구 상자를 미리 로드하는 성능 비용을 발생하지 않고 도구 상자 데이터 공급자를 등록할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolsOptions> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolsOptions> | 예 | 예 | VSPackage를 사용하여 **옵션** 대화 상자가 열려 있는지 확인하고 모든 옵션 페이지의 표시 여부를 새로 고칠 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | 예 | 예 | VSPackage를 사용하여 프로젝트 파일의 변경 내용을 모니터링하고 소스 제어 공급자에 대한 일괄 처리를 제공할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> | 예 | 예 | VSPackage를 사용하여 현재 선택한 프로젝트 항목에 영향을 줄 수 있는 선택 항목에 대한 변경 사항을 IDE에 알립니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelper> | 예 | 예 | 계층 구조(예: 프로젝트 VSPackage)를 사용하여 클립보드 사용을 다른 계층과 조정합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> | 예 | 예 | 도구 창 및 문서 창과 같은 IDE의 UI 요소에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellDocumentWindowMgr> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellDocumentWindowMgr> | 예 | 예 | VSPackage가 데이터 스트림의 내용에 따라 모든 창의 위치를 복원하거나 모든 창의 위치를 스트림에 저장할 수 있습니다. 거의 사용되지 않습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> | 예 | 예 | VSPackage를 사용하면 여러 가지 방법으로 문서를 열고 누가 어떤 문서를 소유하는지 확인할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> | 예 | 예 | <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 인터페이스의 구현자가 오류 및 정보 메시지를 보고하는 데 사용됩니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsWebBrowsingService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsWebBrowsingService> | 예 | 예 | VSPackage가 웹 브라우징 세션을 만들고 제어할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsWebFavorites> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsWebFavorites> | 예 | 예 | VSPackage가 사용자의 즐겨찾기 목록에 추가할 수 **있도록 합니다.** |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsWebPreview> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsWebPreview> | 예 | 예 | VSPackage가 일반적으로 자식 창에서 웹 페이지를 미리 볼 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsWebURLMRU> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsWebURLMRU> | 예 | 예 | VSPackage를 사용하면 가장 최근에 사용한(MRU) URL 목록에 URL을 추가하고 MRU 목록에 있는 모든 URL 목록을 가져올 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsWindowFrame> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> | 예 | 예 | VSPackage가 패키지 또는 패키지의 일부가 위치할 수 있는 창 프레임을 가져올 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsXMLMemberIndexService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsXMLMemberIndexService> | 예 | 예 | 특정 메타데이터 파일과 연결된 XML 형식의 문서 파일에 대한 액세스를 제공합니다. |

## <a name="see-also"></a>참조

- [서비스 사용 및 제공](../../extensibility/using-and-providing-services.md)

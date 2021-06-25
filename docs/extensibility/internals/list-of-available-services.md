---
title: 사용 가능한 서비스 목록 | Microsoft Docs
description: 각 서비스에 대 한 인터페이스를 얻기 위한 서비스 Guid를 비롯 하 여 Visual Studio 및 Visual Studio SDK에서 지 원하는 사용 가능한 서비스 목록을 확인 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- services, Visual Studio
- Visual Studio, services
ms.assetid: 724eb24b-b87c-4971-a2e7-adee7afc03b2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f5ba7fdfd7d86ef9158554d30acdd2995c98e5ec
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899942"
---
# <a name="list-of-available-services"></a>사용 가능한 서비스 목록

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 그리고 Visual Studio SDK는 다음 서비스를 지원 합니다. 일부 패키지는 여기에 나열 되지 않은 고유한 서비스를 제공 합니다. 예를 들어 언어 서비스에는 단일 서비스 GUID가 없습니다. 레지스트리에서 언어 서비스의 GUID를 찾으려면 언어의 이름을 사용 해야 합니다.

여기에 나열 되거나 다른 원본에서 가져온 서비스 Guid (예: 언어 서비스)를 사용 하 여 각 서비스와 함께 표시 되는 기본 인터페이스 또는 인터페이스를 가져옵니다.

## <a name="the-services"></a>서비스

| 서비스 | 인터페이스 | Visual Studio | Visual Studio 2005 | 설명 |
| - | - |---------------|--------------------| - |
| <xref:Microsoft.VisualStudio.OLE.Interop.SBindHost> | <xref:Microsoft.VisualStudio.OLE.Interop.IBindHost> | 예 | 예 | Vspackage에서 <xref:Microsoft.VisualStudio.OLE.Interop.IBindHost> ActiveX 컨트롤의 인터페이스를 가져와 비동기 데이터 전송을 용이 하 게 하는 데 사용 됩니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SDTE> | <xref:EnvDTE.DTE> | 아니요 | 예 | 자동화에 사용 되는 DTE (디자인 타임 확장성) 개체를 가져옵니다.<br /><br /> C/C + + ID: SID_SDTE |
| <xref:Microsoft.VisualStudio.Shell.Interop.SCodeNavigate> | <xref:Microsoft.VisualStudio.Shell.Interop.ICodeNavigate> | 예 | 예 | 컨트롤에 대 한 기본 이벤트 처리기를 표시 하기 위해 forms 디자이너에서 구현 합니다. |
| <xref:Microsoft.VisualStudio.OLE.Interop.SContainerDispatch> | IDispatch | 예 | 예 | VSPackage가 다른 VSPackage 또는 컨트롤의 자동화 인터페이스에 액세스할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SExtendedTypeLib> | <xref:Microsoft.VisualStudio.Shell.Interop.IExtendedTypeLib> | 예 | 예 | VSPackage가 확장 형식 라이브러리를 추가 하거나 만들 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SDirList> | <xref:Microsoft.VisualStudio.Shell.Interop.IDirList> | 아니요 | 예 | 컨테이너의 명명 된 목록 목록에 대 한 액세스를 제공 합니다. 예를 들어 **찾는 위치** 드롭다운 목록의 **찾기 및 바꾸기** 대화 상자에 표시 된 대로 검색할 디렉터리 목록입니다. <xref:Microsoft.VisualStudio.Shell.Interop.IDirList>개체는에서 읽고 쓸 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SIVsPackageDynamicToolOwner> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwner> | 예 | 예 | VSPackage에서 자체 도구 창을 동적으로 표시 하거나 숨길 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SLicensedClassManager> | <xref:Microsoft.VisualStudio.Shell.Interop.ILicensedClassManager> | 예 | 예 | 라이선스 키 목록을 지정 하 여 VSPackage가 필요한 클래스를 나타낼 수 있도록 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . |
| <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> | <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> | 예 | 예 | VSPackage가 로컬 레지스트리 하이브에 상대적인 레지스트리에 액세스할 수 있도록 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . |
| <xref:Microsoft.VisualStudio.OLE.Interop.SOleComponentManager> | <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager> | 예 | 예 | 메시지 루프, 키보드 루프 및 이벤트 알림과 같은 구성 요소 조정 서비스를 제공 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> | 예 | 예 | VSPackage가 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 도움말, 상태 표시줄 및 ui 이벤트와 같은의 다양 한 ui (사용자 인터페이스) 요소에 액세스할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SOleInPlaceComponent> | <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> | 예 | 예 | VSPackage에서 ui를의 UI와 통합할 수 있도록 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SOleInPlaceComponentSite> | <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentSite> | 예 | 예 | VSPackage를 사용 하 여 도구와 관련 된 UI 변경을 제어할 수 있습니다. |
| <xref:Microsoft.VisualStudio.OLE.Interop.SOleUndoManager> | <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> | 예 | 예 | VSPackage가 컨테이너의 실행 취소 스택에 참여 하거나 해당 컨테이너의 실행 취소 스택에 액세스 하기 위해 컨테이너의 실행 취소 관리자에 액세스할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService> | <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> | 예 | 예 | VSPackage에서 자체 서비스를 제공할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SProfferTypeLib> | <xref:Microsoft.VisualStudio.Shell.Interop.IProfferTypeLib> | 예 | 예 | Forms 디자이너를 사용 하 여 형식 라이브러리를 참조할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> | <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> | 예 | 예 | 선택 컨테이너에서 선택 항목에 대 한 액세스를 제공 합니다. Forms 디자이너에서 사용 됩니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SUIHostCommandDispatcher> | <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> | 예 | 예 | VSPackage가 IDE (통합 개발 환경)를 대신 하 여 명령 처리기 체인에 참여 하 고 명령을 처리할 수 있게 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SUIHostLocale> | <xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale> | 예 | 예 | 호스트의 UI 로캘 정보에 대 한 액세스를 제공 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> | 아니요 | 예 | 로깅이 설정 된 경우 VSPackage에서 높은 수준의 메시지를 기록할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddProjectItemDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg> | 예 | 예 | Vspackage에서 자체 **항목 추가** 메뉴 옵션을 구현할 수 있도록 **프로젝트 항목 추가** 대화 상자에 대 한 액세스를 제공 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg> | 예 | 예 | **참조 추가** 대화 상자를 표시 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> | 예 | 예 | VSPackage를 사용 하 여 명령줄 스위치가 devenv.exe에 제공 되었는지 여부를 확인할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCallBrowser> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCallBrowser> | 아니요 | 예 | VSPackage를 사용 하 여 디버깅에 사용 되는 새 **호출 브라우저** 를 만들 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsClassView> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsClassView> | 예 | 예 | VSPackage가 **클래스 뷰** 를 특정 개체와 동기화 할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCmdNameMapping> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCmdNameMapping> | 예 | 예 | 는 명령 이름을 Guid에 매핑하고 다시 사용 가능한 모든 명령 및 이름의 이름을 결정 하는 기능을 지원 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCodeDefView> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCodeDefView> | 아니요 | 예 | VSPackage를 사용 하 여 **코드 정의 보기** 를 조작할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCodeShareHandler> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCodeShareHandler> | 예 | 예 | 내부 서비스. 사용하지 마십시오. |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsCodeWindow> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> | 예 | 예 | 하나 이상의 문서를 포함할 수 있는 코드 창에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsCodeWindowManager> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> | 예 | 예 | VSPackage가 드롭다운 막대와 같은 코드 창에 변경 내용을 추가할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCommandWindow> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindow><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindow2> | 예 | 예 | VSPackage가 **명령 창을** 통해 명령을 실행하고, 그렇지 않으면 명령 **창** 와 상호 작용할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCommandWindowsCollection> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommandWindowsCollection> | 아니요 | 예 | VSPackage가 에서 유지 관리하는 **명령** 창 목록을 조작할 수 있도록 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsComplusLibrary> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibraryReferenceManager> | 예 | 예 | VSPackage가 **개체 브라우저** 에 찾아보기 정보를 제공할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsComponentSelectorDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsComponentSelectorDlg> | 아니요 | 예 | 사용자가 프로젝트에 추가할 외부 구성 요소를 선택할 수 있는 **참조 추가** 옵션을 지원하도록 VSPackage를 사용하도록 설정합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsComponentSelectorDlg2> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsComponentSelectorDlg2> | 아니요 | 예 | 사용자가 프로젝트에 추가할 외부 구성 요소를 선택할 수 있는 **참조 추가** 옵션을 지원하도록 VSPackage를 사용하도록 설정합니다. 이 버전의 대화 상자에서는 구성 요소 목록을 표시하기 전에 미리 채울 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsConfigurationManagerDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsConfigurationManagerDlg> | 아니요 | 예 | **구성 관리자** 대화 상자를 표시합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject> | 아니요 | 예 | VSPackage가 다른 프로젝트의 컬렉션을 포함하는 프로젝트를 만들 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsDebuggableProtocol> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProtocol> | 예 | 예 | VSPackage가 IDE에서 특정 디버그 엔진을 시작하는 데 사용하는 디버깅 가능한 프로토콜 목록을 업데이트할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsDebugLaunch> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugLaunch> | 예 | 예 | VSPackage에서 디버거를 시작할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsDiscoveryService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService> | 예 | 예 | VSPackage가 웹 서비스를 검색하는 데 사용되는 검색 세션을 만들 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsEnumHierarchyItemsFactory> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumHierarchyItemsFactory> | 예 | 예 | <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumHierarchyItemsFactory>지정된 계층(프로젝트)을 열거하는 데 사용되는 개체를 만드는 팩터리 를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsErrorList> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsErrorList> | 아니요 | 예 | **빌드 오류 목록** 작업 창을 조작하기 위한 추가 메서드를 제공합니다. 특히 는 **빌드 오류 목록** 작업 창을 전면에 표시하고 모든 오류를 강제로 표시합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager> | 예 | 예 | 현재 솔루션의 **기타 파일** 프로젝트 노드에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChange> | | 예 | 예 | 사용되지 않습니다. `SVsFileChangeEx`대신 서비스를 사용하세요. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> | 예 | 예 | VSPackage가 IDE에 의해 트리거되는 다양한 파일 변경 이벤트에 액세스할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFilterAddProjectItemDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> | 예 | 예 | VSPackage가 **항목 추가** 대화 상자에 표시되는 항목을 필터링할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFilterKeys> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterKeys> | 예 | 예 | VSPackage가 고급 키보드 필터링을 수행할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFontAndColorCacheManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> | 아니요 | 예 | 의 글꼴 및 색에 대한 캐시 집합에 대한 액세스를 제공하여 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 특정 캐시 또는 모든 캐시를 새로 고치거나 지웁니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsFontAndColorStorage> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities> | 예 | 예 | VSPackage가 에서 유지 관리하는 글꼴 및 색 설정을 조작할 수 있도록 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 합니다. 또한 이 서비스는 글꼴 및 색 데이터를 조작하기 위한 유틸리티 메서드 컬렉션에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> | 예 | 예 | 일반 **출력 창** 창에 대한 액세스를 제공하여 필요에 따라 만듭니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsHelpService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsHelpSystem> | 예 | 예 | 도움말 시스템에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsHTMLConverter> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsHTMLConverter> | 예 | 예 | [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]디버거에서 HTML을 처리하여 출력 형식을 지정하는 데 사용됩니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIME> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsIME> | 예 | 예 | VSPackage 내에서 IME(입력 메서드 편집기) API에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIntegratedHelp> | <xref:Microsoft.VisualStudio.VSHelp.SVsHelp> | 예 | 예 | 도움말 파일을 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 통한 탐색 제어뿐만 아니라 키워드 또는 URL 액세스에 대한 도움말 시스템에 대한 액세스를 제공합니다. 이 서비스는 도움말이 IDE에 통합되고 외부 프로그램으로 실행되지 않는 경우에만 사용할 수 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIntelliMouseHandler> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntelliMouseHandler> | 예 | 예 | VSPackage가 마우스 휠을 사용하고 마우스 휠을 클릭할 때 스크롤 및 이동 비트맵 처리와 같은 IntelliMouse 기능에 액세스할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseEngine> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseEngine> | 아니요 | 예 | 프로젝트 계층 노드가 IntelliSense 작업에 대한 지원의 일부로 파일을 로드하거나 언로드할 수 있도록 합니다. 로드 및 언로드 프로세스는 프로젝트의 IntelliSense 도구 설명에 표시되는 내용에 영향을 줄 수 있는 이벤트를 트리거합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseProjectHost> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProjectHost> | 아니요 | 예 | 프로젝트 계층 노드가 IntelliSense 도구 설명에 표시될 수 있는 중첩된 IntelliSense 프로젝트(인터페이스를 구현하는)에 대한 정보를 제공할 수 있도록 <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsIntellisenseProjectManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProjectManager> | 아니요 | 예 | 프로젝트 계층 노드가 IntelliSense 도구 설명에 표시되는 내용에 영향을 줄 수 있는 참조 또는 구성 변경과 같은 이벤트를 수신기에 알릴 수 있도록 합니다. 포함된 언어와 함께 사용할 수 있도록 설계되었습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsInvisibleEditorManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> | 예 | 예 | VSPackage에서 "보이지 않는" 편집기 즉, 전체 편집 기능을 제공 하지만 사용자에 게 표시 되지 않는 편집기를 등록할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsLanguageFilter> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> | 예 | 예 | VSPackage를 사용 하 여 데이터 팁과 단어 범위와 같은 추가 정보를 텍스트 뷰에 제공할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsLaunchPad> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPad> | 예 | 예 | VSPackage에서 임시 일괄 처리 스크립트를 실행 하 고 출력이 출력 창으로 전송 되는 명령줄 프로그램을 실행 하 고 오류 창으로 전송 되는 표준 경고 및 오류 메시지를 구문 분석할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsLaunchPadFactory> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPadFactory> | 예 | 예 | 개체를 만들기 위한 팩터리를 제공 <xref:Microsoft.VisualStudio.Shell.Interop.IVsLaunchPad> 합니다. |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsLinkedUndoTransactionManager> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> | 예 | 예 | 연결 된 실행 취소 관리자에 대 한 액세스를 제공 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsMenuEditor> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsMenuEditorFactory> | 예 | 예 | Forms 디자이너에서 공유 메뉴 편집기에 액세스할 수 있습니다. IVsMenuEditorFactory를 쿼리할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMenuEditor> . |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> | 예 | 예 | VSPackage를 사용 하 여 특정 컨텍스트에 대 한 도움말 키워드를 연결 하는 데 사용 되는 "컨텍스트 모음"을 만들 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjBrowser> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjBrowser> | 예 | 예 | VSPackage가 **개체 브라우저** 의 특정 개체로 이동할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager> | 예 | 예 | VSPackage를 사용 하 여 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 네임 스페이스, 클래스, 열거형 등의 개체를 관리 하기 위해 라이브러리 관리자를에 등록할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectSearch> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectSearch> | 예 | 예 | VSPackage에서 특정 개체를 검색할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsOpenProjectOrSolutionDlg> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsOpenProjectOrSolutionDlg> | 아니요 | 예 | VSPackage가 표준 대화 상자를 사용 하 여 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트 또는 솔루션을 열 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> | 예 | 예 | VSPackage를 사용 하 여 일반 출력 창에 추가 출력 창을 만들 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsParseCommandLine> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsParseCommandLine> | 예 | 예 | 인터페이스의 구현 자가 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 명령줄을 구문 분석할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsPathVariableResolver> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsPathVariableResolver> | 아니요 | 예 | [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]최종 경로를 생성 하기 위해 경로에 포함 된와 관련 된 변수를 확인 하는 방법을 제공 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsPreviewChangesService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsPreviewChangesService> | 아니요 | 예 | 리팩터링 코드에 사용 되는 **변경 내용 미리 보기** 대화 상자를 표시 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsProfileDataManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsProfileDataManager> | 아니요 | 예 | [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]현재 사용자의 프로필 설정에 대 한 UI를 표시 하는 것 뿐만 아니라 설정 데이터를 가져오고 내보낼 수 있도록 하는 프로필 관리자에 대 한 액세스를 제공 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsProfilesManagerUI> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsProfilesManagerUI> | 아니요 | 예 | 현재 사용자의 프로필 설정을 보여 주는 대화 상자를 표시 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsPropertyPageFrame> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPageFrame> | 예 | 예 | VSPackage를 사용 하 여 **속성** 창에 처음 표시 되는 속성 페이지를 재정의할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | 아니요 | 예 | Vspackage에서 파일을 메모리에서 변경 하거나 저장 하는 것을 소스 제어 공급자에 게 알리기 위해 사용 됩니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterDebugTargetProvider> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectDebugTargetProvider> | 아니요 | 예 | VSPackage 프로젝트를 사용 하 여 디버거에서 시작할 대상을 프로그래밍 방식으로 재정의할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors> | 예 | 예 | VSPackage가 IDE에 편집기 팩터리를 등록할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsRegisterFindScope> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsRegisterFindScope> | 아니요 | 예 | VSPackage **에서 파일에서 찾기** 대화 상자에 대 한 검색 범위를 등록할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterPriorityCommandTarget> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget> | 예 | 예 | VSPackage가 자신을 우선 순위가 높은 명령 처리기로 등록 하 여 VSPackage가 모든 명령을 볼 수 있도록 합니다. 모든 경우에만 사용 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes> | 예 | 예 | VSPackage가 IDE에 프로젝트 형식을 등록할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsResourceManager> | 아니요 | 예 | VSPackage가 위성 Dll에서 관리 되는 리소스와 관리 되지 않는 리소스를 로드할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceView> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsResourceView> | 예 | 예 | <xref:Microsoft.VisualStudio.Shell.Interop.SVsClassView>대신 서비스를 사용 하십시오. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> | 예 | 예 | 현재 열려 있는 모든 문서를 추적 하는 IDE의 실행 중인 문서 테이블 (RDT)에 대 한 액세스를 제공 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | 아니요 | 예 | 소스 제어에 참여할 수 있도록 Vspackage에서 소스 제어 공급자에 직접 등록할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccToolsOptions> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | 예 | 예 | VSPackage에서 소스 제어 공급자 옵션을 가져오고 설정할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSettingsReader> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> | 아니요 | 예 | 사용자의 프로필 설정에 대 한 읽기 액세스를 제공 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell> | 예 | 예 | VSPackage가 다른 Vspackage와 직접 상호 작용 하 고 조작할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger> | 예 | 예 | 디버거에 대 한 액세스를 제공 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> | 예 | 예 | VSPackage를 사용 하 여 현재 선택 영역에 액세스 하 고 명령 UI 컨텍스트를 관리할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVSMDCodeDomProvider> | IVSMDCodeDomProvider | 아니요 | 예 | 네이티브 코드에서 사용할 수 있는 코드 DOM(문서 개체 모델) 공급자에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVSMDDesignerService> | IVSMDCodeDomCreator<br /><br /> IVSMDDesignerService | 아니요 | 예 | 관리되는 양식 디자이너에 대한 IDE 지원에 대한 액세스를 제공합니다. `IVSMDCodeDomCreator`코드 DOM 공급자를 만드는 데 사용할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVSMDPropertyBrowser> | IVSMDPropertyBrowser | 아니요 | 예 | 디자이너 속성 Windows 서비스에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVSMDTypeResolutionService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVSMDTypeResolutionService> | 아니요 | 예 | 네이티브 코드에서 사용할 수 있는 개체를 반환할 수 있는 인터페이스에 대한 액세스를 <xref:System.ComponentModel.Design.ITypeResolutionService> 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSmartOpenScope> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSmartOpenScope> | 아니요 | 예 | 필요에 따라 잠금을 고려하여 어셈블리에서 범위를 여는 방법을 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> | 예 | 예 | 현재 솔루션에 대한 최상위 액세스 권한을 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager> | 예 | 예 | VSPackage가 솔루션의 빌드 프로세스와 상호 작용할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionObject> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> | 예 | 예 | 대신 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> 서비스를 사용하세요. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionPersistence> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> | 예 | 예 | VSPackage가 현재 솔루션의 .sln 파일에서 정보를 저장하고 검색할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsSQLCLRReferences> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsSQLCLRReferences> | 아니요 | 예 | 관리 코드 어셈블리에서 참조를 추가하고 업데이트하는 기능을 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsStartPageDownload> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsStartPageDownload> | 아니요 | 예 | 백그라운드 스레드에서 다운로드 서비스를 시작 및 중지하기 위한 Visual Studio 2017 시작 페이지의 다운로드 서비스에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> | 예 | 예 | IDE의 상태 표시줄에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsStrongNameKeys> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsStrongNameKeys> | 아니요 | 예 | 관리 코드 어셈블리 서명에 사용되는 암호를 사용하여 강력한 키 이름 및 키 파일을 만드는 메서드에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsStructuredFileIO> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsStructuredFileIO> | 예 | 예 | VSPackage에서 데이터를 여러 형식으로 저장할 수 있도록 지원합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> | 예 | 예 | IDE의 작업 목록 창에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextImageUtilities> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextImageUtilities> | 아니요 | 예 | 텍스트 파일을 로드하고 저장하기 위한 유틸리티를 제공합니다. |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> | 예 | 예 | IDE에서 사용할 수 있는 숨겨진 텍스트 세션(숨겨진 영역의 경우)뿐만 아니라 모든 텍스트 버퍼에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsTextOut> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsTextOut> | 예 | 예 | 디바이스 컨텍스트에 텍스트를 쓰기 위한 Win32 함수 버전을 `TextOut` 제공합니다(DC 핸들 필요). |
| <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextSpanSet> | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextSpanSet> | 예 | 예 | 텍스트 이미지 또는 버퍼의 텍스트 범위 목록에 대한 액세스를 제공합니다. 이 서비스는 일반적으로 문서 컨테이너에서 구현되며 현재 문서를 참조합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsThreadedWaitDialog> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsThreadedWaitDialog> | 아니요 | 예 | VSPackage가 백그라운드 작업을 기다리는 데 사용되는 다른 스레드에서 대기하는 대화 상자를 표시할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsThreadPool> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsThreadPool> | 아니요 | 예 | VSPackage가 에서 유지 관리되는 백그라운드 작업을 시작할 수 있도록 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox> | 예 | 예 | IDE의 **도구 상자** 에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolboxActiveXDataProvider> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider> | 예 | 예 | VSPackage가 **도구 상자** 항목에서 정보를 가져올 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolboxDataProviderRegistry> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProviderRegistry> | 아니요 | 예 | VSPackage가 전체 도구 상자 를 미리 로드하는 데 드는 성능 비용을 발생시키지 않고 도구 상자 데이터 공급자를 **등록할 수** 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolsOptions> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolsOptions> | 아니요 | 예 | VSPackage를 사용하여 **옵션** 대화 상자가 열려 있는지 확인하고 모든 옵션 페이지의 표시 여부를 새로 고칠 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | 아니요 | 예 | VSPackage가 프로젝트 파일의 변경 내용을 모니터링하고 소스 제어 공급자에 대한 일괄 처리 제어를 제공할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> | 예 | 예 | VSPackage가 현재 선택한 프로젝트 항목에 영향을 줄 수 있는 선택 항목에 대한 변경 내용을 IDE에 알릴 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelper> | 예 | 예 | 계층 구조(예: 프로젝트 VSPackage)에서 클립보드 사용을 다른 계층과 조정할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> | 예 | 예 | 도구 창 및 문서 창과 같은 IDE의 UI 요소에 대한 액세스를 제공합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellDocumentWindowMgr> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellDocumentWindowMgr> | 예 | 예 | VSPackage가 데이터 스트림의 내용에 따라 모든 창의 위치를 복원하거나 모든 창의 위치를 스트림에 저장할 수 있도록 합니다. 거의 사용되지 않습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> | 예 | 예 | VSPackage가 다양한 방법으로 문서를 열고 누가 어떤 문서를 소유하는지 확인할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> | 아니요 | 예 | 인터페이스의 구현자가 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 오류 및 정보 메시지를 보고하는 데 사용됩니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsWebBrowsingService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsWebBrowsingService> | 예 | 예 | VSPackage가 웹 검색 세션을 만들고 제어할 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsWebFavorites> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsWebFavorites> | 예 | 예 | VSPackage를 사용하여 사용자의 **즐겨찾기** 목록에 추가할 수 있습니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsWebPreview> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsWebPreview> | 예 | 예 | VSPackage가 일반적으로 자식 창에서 웹 페이지를 미리 볼 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsWebURLMRU> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsWebURLMRU> | 예 | 예 | VSPackage가 URL의 MRU(가장 최근에 사용) 목록에 URL을 추가하고 MRU 목록의 모든 URL 목록을 가져올 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsWindowFrame> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> | 예 | 예 | VSPackage가 패키지 또는 패키지의 일부가 배치될 수 있는 창 프레임을 가져올 수 있도록 합니다. |
| <xref:Microsoft.VisualStudio.Shell.Interop.SVsXMLMemberIndexService> | <xref:Microsoft.VisualStudio.Shell.Interop.IVsXMLMemberIndexService> | 예 | 예 | 특정 메타데이터 파일과 연결된 XML 형식 설명서 파일에 대한 액세스를 제공합니다. |

## <a name="see-also"></a>참조

- [서비스 사용 및 제공](../../extensibility/using-and-providing-services.md)

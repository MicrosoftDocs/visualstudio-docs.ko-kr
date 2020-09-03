---
title: Visual Studio SDK 내 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e72020795bc3181e11f0f90eff580a2365d4000
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707583"
---
# <a name="inside-the-visual-studio-sdk"></a>Visual Studio SDK 기본 사항

이 섹션에서는 visual studio 아키텍처, 구성 요소, 서비스, 스키마, 유틸리티 등을 비롯 한 Visual Studio 확장에 대 한 자세한 정보를 제공 합니다.

## <a name="extensibility-architecture"></a>확장성 아키텍처
 다음 그림에서는 Visual Studio 확장성 아키텍처를 보여 줍니다. Vspackage는 IDE에서 서비스로 공유 되는 응용 프로그램 기능을 제공 합니다. 또한 표준 IDE는 IDE 창 고 기능에 대 한 액세스를 제공 하는와 같은 광범위 한 서비스를 제공 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> .

 ![환경 아키텍처 그래픽](../../extensibility/internals/media/environment.gif "environment") Visual Studio 아키텍처의 일반화 된 보기

## <a name="vspackages"></a>VSPackages
 VSPackage는 UI 요소, 서비스, 프로젝트, 편집기 및 디자이너를 사용하여 Visual Studio를 구성 및 확장하는 소프트웨어 모듈입니다. Vspackage는 Visual Studio의 중앙 아키텍처 단위입니다. 자세한 내용은 [VSPackages](../../extensibility/internals/vspackages.md)을 참조하세요.

## <a name="visual-studio-shell"></a>Visual Studio Shell
 Visual Studio shell은 기본 기능을 제공 하 고 해당 구성 요소 Vspackage 및 MEF 확장 간의 교차 통신을 지원 합니다. 자세한 내용은 [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md)을 참조 하세요.

## <a name="user-experience-guidelines"></a>사용자 환경 지침
 Visual Studio의 새로운 기능을 디자인할 계획인 경우 디자인 및 유용성 팁에 대 한 다음 지침을 확인 해야 합니다. [Visual Studio 사용자 환경 지침](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="commands"></a>명령
 명령은 문서 인쇄, 보기 새로 고침 또는 새 파일 만들기 등의 작업을 수행하는 함수입니다.

 Visual Studio를 확장 하는 경우 명령을 만들고 Visual Studio shell을 사용 하 여 등록할 수 있습니다. 이러한 명령이 IDE에 표시 되는 방식 (예: 메뉴 또는 도구 모음)을 지정할 수 있습니다. 일반적으로 **도구** 메뉴에 사용자 지정 명령이 표시 되 고 도구 창을 표시 하는 명령이 **보기** 메뉴의 **다른 창** 하위 메뉴에 표시 됩니다.

 명령을 만들 때이에 대 한 이벤트 처리기도 만들어야 합니다. 이벤트 처리기는 명령이 표시 되거나 활성화 되는 시점을 결정 하 고,이를 통해 텍스트를 수정할 수 있으며, 활성화 될 때 명령이 적절히 응답 하도록 보장할 수 있습니다. 대부분의 경우 IDE는 인터페이스를 사용 하 여 명령을 처리 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . Visual Studio의 명령은 로컬 선택 항목에 따라 가장 안쪽의 명령 컨텍스트에서 시작 하 여 전역 선택에 따라 가장 바깥쪽 컨텍스트로 진행 됩니다. 주 메뉴에 추가된 명령은 즉시 스크립팅에 사용할 수 있습니다.

 자세한 내용은 [명령, 메뉴 및 도구 모음](../../extensibility/internals/commands-menus-and-toolbars.md)을 참조 하세요.

## <a name="menus-and-toolbars"></a>메뉴 및 도구 모음
 메뉴와 도구 모음은 사용자가 명령을 호출할 수 있는 방법을 제공 합니다. 메뉴는 일반적으로 도구 창 맨 위에 개별 텍스트 항목으로 표시 되는 명령의 행 또는 열입니다. 하위 메뉴는 사용자가 작은 화살표를 포함 하는 명령을 클릭할 때 표시 되는 보조 메뉴입니다. 사용자가 특정 UI 요소를 마우스 오른쪽 단추로 클릭 하면 상황에 맞는 메뉴가 나타납니다. 일반적인 메뉴 이름에는 **파일**, **편집**, **보기**, **창**등이 있습니다. 자세한 내용은 [메뉴 및 명령 확장](../../extensibility/extending-menus-and-commands.md)을 참조 하세요.

 도구 모음은 단추와 콤보 상자, 목록 상자 및 텍스트 상자와 같은 다른 컨트롤의 행 또는 열입니다. 일반적으로 도구 모음 단추에는 **파일 열기** 명령에 대 한 폴더 아이콘 또는 **인쇄** 명령의 프린터와 같은 아이콘 이미지가 있습니다. 모든 도구 모음 요소는 명령과 연결 됩니다. 도구 모음 단추를 클릭 하면 연결 된 명령이 실행 됩니다. 드롭다운 컨트롤의 경우 드롭다운 목록의 각 항목은 다른 명령과 연결 되어 있습니다. 분할자 컨트롤과 같은 일부 toolbar 컨트롤은 hybrids입니다. 컨트롤의 한 쪽은 도구 모음 단추이 고 다른 쪽은 클릭 하면 여러 명령을 표시 하는 아래쪽 화살표입니다.

## <a name="tool-windows"></a>도구 창
 도구 창은 IDE에서 정보를 표시 하는 데 사용 됩니다. 도구 **상자**, **솔루션 탐색기**, **속성** 창 및 **웹 브라우저** 는 도구 창의 예입니다.

 도구 창은 일반적으로 사용자가 상호 작용할 수 있는 다양 한 컨트롤을 제공 합니다. 예를 들어 **속성** 창을 사용 하면 사용자가 특정 용도를 제공 하는 개체의 속성을 설정할 수 있습니다. **속성** 창은 이러한 점에서 특수 하지만 여러 상황에서 사용할 수 있기 때문에 일반적 이기도 합니다. 마찬가지로, Visual Studio에서 많은 하위 시스템을 사용 하 여 Visual Studio 사용자에 게 출력을 제공할 수 있기 때문에 **출력** 창은 텍스트 기반 출력을 제공 하기 때문에 특수 합니다.

 몇 가지 도구 창을 포함 하는 Visual Studio의 다음 그림을 참조 하세요.

 ![스크린샷](../../extensibility/internals/media/t1gui.png "T1gui")

 일부 도구 창은 솔루션 탐색기 도구 창을 표시 하 고 다른 도구 창을 숨기는 단일 창에 함께 도킹 되지만 탭을 클릭 하 여 사용할 수 있습니다. 이 그림에서는 두 개의 다른 도구 창, **오류 목록** 및 **출력** 창을 보여 줍니다. 단일 창에 함께 도킹 됩니다.

 또한 몇 가지 편집기 창이 표시 되는 주 문서 창이 표시 됩니다. 도구 창에는 일반적으로 하나의 인스턴스만 있지만 (예: 하나의 **솔루션 탐색기**만 열 수 있음) 편집기 창에는 여러 인스턴스가 포함 될 수 있습니다. 각 인스턴스는 개별 문서를 편집 하는 데 사용 되지만 모두 동일한 창에 도킹 됩니다. 이 그림에서는 두 개의 편집기 창, 폼 디자이너 창이 있는 문서 창을 보여 줍니다. 문서 창의 모든 창은 탭을 클릭 하 여 사용할 수 있지만 EditorPane.cs 파일이 포함 된 편집기 창이 표시 되 고 활성화 됩니다.

 Visual Studio를 확장 하는 경우 Visual Studio 사용자가 확장과 상호 작용할 수 있도록 하는 도구 창을 만들 수 있습니다. Visual Studio 사용자가 문서를 편집 하는 데 사용할 수 있는 고유한 편집기를 만들 수도 있습니다. 도구 창과 편집기가 Visual Studio에 통합 되기 때문에 사용자가 탭에 고정 하거나 탭에 표시 하기 위해 프로그래밍할 필요가 없습니다. Visual Studio에 올바르게 등록 된 경우 Visual Studio에서 도구 창 및 문서 창의 일반적인 기능이 자동으로 제공 됩니다. 자세한 내용은 [도구 창 확장 및 사용자 지정](../../extensibility/extending-and-customizing-tool-windows.md)을 참조 하세요.

## <a name="document-windows"></a>문서 창
 문서 창은 MDI (다중 문서 인터페이스) 창의 프레임 있는 자식 창입니다. 문서 창은 일반적으로 텍스트 편집기, 폼 편집기 (디자이너 라고도 함)를 호스트 하거나 컨트롤을 편집 하는 데 사용 되지만 다른 기능 형식을 호스팅할 수도 있습니다. **새 파일** 대화 상자에는 Visual Studio에서 제공 하는 문서 창의 예가 포함 되어 있습니다.

 대부분의 편집기는 프로그래밍 언어 또는 HTML 페이지, 프레임셋, c + + 파일, 헤더 파일 등의 파일 형식에만 적용 됩니다. **새 파일** 대화 상자에서 템플릿을 선택 하면 사용자가 템플릿에 연결 된 파일 형식에 대 한 편집기의 문서 창을 동적으로 만듭니다. 문서 창은 사용자가 기존 파일을 열 때에도 생성 됩니다.

 문서 창은 MDI 클라이언트 영역으로 제한 됩니다. 각 문서 창에는 위쪽에 탭이 있고 탭 순서는 MDI 영역에 열려 있을 수 있는 다른 창에 연결 되어 있습니다. 문서 창의 탭을 마우스 오른쪽 단추로 클릭 하면 MDI 영역을 여러 개의 가로 또는 세로 탭 그룹으로 분할 하는 옵션이 포함 된 바로 가기 메뉴가 표시 됩니다. MDI 영역을 분할 하면 여러 파일을 동시에 볼 수 있습니다. 자세한 내용은 [문서 창](../../extensibility/internals/document-windows.md)을 참조 하세요.

## <a name="editors"></a>편집기
 Visual Studio 편집기를 사용 하 여 사용자 지정 하 고 MEF (Managed Extensibility Framework)를 통해 고유한 콘텐츠 형식에 사용할 수 있습니다. 대부분의 경우 편집기를 확장 하기 위해 VSPackage를 만들 필요가 없습니다. 하지만 셸에서 기능 (예: 메뉴 명령 또는 바로 가기 키)을 포함 하려는 경우 MEF 확장을 VSPackage와 결합할 수 있습니다.

 사용자 지정 편집기를 만들 수도 있습니다. 예를 들어 데이터베이스에 대 한 읽기 및 쓰기를 하려는 경우 나 디자이너를 사용 하려는 경우입니다. 메모장 이나 Microsoft 워드 패드와 같은 외부 편집기를 사용할 수도 있습니다. 자세한 내용은 [편집기 및 언어 서비스 확장](../../extensibility/editor-and-language-service-extensions.md)을 참조 하세요.

## <a name="language-services"></a>언어 서비스
 Visual Studio 편집기에서 새 프로그래밍 키워드를 지원 하거나 새 프로그래밍 언어를 지원 하려면 언어 서비스를 만듭니다. 각 언어 서비스는 특정 편집기 기능을 완전히, 부분적으로 또는 전혀 구현 하지 않을 수 있습니다. 구성 된 방법에 따라 언어 서비스에서 편집기의 구문 강조 표시, 중괄호 일치, IntelliSense 지원 및 기타 기능을 제공할 수 있습니다.

 언어 서비스의 핵심은 파서 및 스캐너입니다. 스캐너 (또는 렉서)는 소스 파일을 토큰으로 알려진 요소로 나누고, 파서는 이러한 토큰 간의 관계를 설정 합니다. 언어 서비스를 만들 때 Visual Studio에서 언어의 토큰과 문법을 이해할 수 있도록 파서와 스캐너를 구현 해야 합니다. 관리 되거나 관리 되지 않는 언어 서비스를 만들 수 있습니다. 자세한 내용은 [레거시 언어 서비스 확장성](../../extensibility/internals/legacy-language-service-extensibility.md)을 참조 하세요.

## <a name="projects"></a>프로젝트

Visual Studio에서 프로젝트는 개발자가 소스 코드 및 기타 리소스를 구성 하 고 작성 하는 데 사용 하는 컨테이너입니다. 프로젝트를 사용 하 여 소스 코드, 웹 서비스 및 데이터베이스에 대 한 참조 및 기타 리소스를 구성, 빌드, 디버그 및 배포할 수 있습니다. Vspackage는 프로젝트 형식, 프로젝트 하위 형식 및 사용자 지정 도구를 제공 하 여 Visual Studio 프로젝트 시스템을 확장할 수 있습니다.

응용 프로그램을 만들기 위해 함께 작동 하는 하나 이상의 프로젝트를 그룹화 한 *솔루션*에서 프로젝트를 함께 수집할 수도 있습니다. 솔루션과 관련 된 프로젝트 및 상태 정보는 두 개의 솔루션 파일, 텍스트 기반 [솔루션 (.sln) 파일](solution-dot-sln-file.md) 및 이진 [솔루션 사용자 옵션 (.suo) 파일](solution-user-options-dot-suo-file.md)에 저장 됩니다. 이러한 파일은 이전 버전의 Visual Basic에서 사용 된 그룹 파일 (dsw)과 유사 하며, 이전 버전의 c + +에서 사용 된 작업 영역 (.) 및 사용자 옵션 (opt) 파일입니다.

자세한 내용은 [프로젝트](../../extensibility/internals/projects.md) 및 [솔루션](../../extensibility/internals/solutions-overview.md)을 참조 하세요.

## <a name="project-and-item-templates"></a>프로젝트 및 항목 템플릿
 Visual Studio에는 미리 정의 된 프로젝트 템플릿과 프로젝트 항목 템플릿이 포함 되어 있습니다. 사용자 고유의 템플릿을 만들거나 커뮤니티에서 템플릿을 가져온 후 Visual Studio에 통합할 수도 있습니다. [MSDN 코드 갤러리](https://code.msdn.microsoft.com/site/search?query=visual%20studio) 는 템플릿 및 확장에 사용할 수 있는 위치입니다.

 템플릿에는 특정 종류의 응용 프로그램, 컨트롤, 라이브러리 또는 클래스를 빌드하는 데 필요한 프로젝트 구조와 기본 파일이 포함 되어 있습니다. 템플릿 중 하 나와 비슷한 소프트웨어를 개발 하려는 경우 템플릿을 기반으로 하는 프로젝트를 만든 다음 해당 프로젝트의 파일을 수정 합니다.

> [!NOTE]
> 이 템플릿 아키텍처는 프로젝트에 대해 지원 되지 않습니다 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] .

 자세한 내용은 [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)를 참조 하세요.

## <a name="properties-and-options"></a>속성 및 옵션
 **속성** 창에는 단일 또는 여러 개의 선택 된 항목의 속성이 표시 됩니다. [속성 확장](../../extensibility/internals/extending-properties.md) 옵션 페이지에는 프로그래밍 언어 또는 VSPackage: [옵션 및 옵션 페이지](../../extensibility/internals/options-and-options-pages.md)와 같은 특정 구성 요소와 관련 된 옵션 집합이 포함 되어 있습니다. 설정은 일반적으로 가져오고 내보낼 수 있는 UI 관련 기능입니다. [사용자 설정에 대 한 지원](../../extensibility/internals/support-for-user-settings.md)입니다.

## <a name="visual-studio-services"></a>Visual Studio 서비스
 서비스는 사용할 구성 요소에 대 한 특정 인터페이스 집합을 제공 합니다. Visual Studio는 확장을 포함 하 여 모든 구성 요소에서 사용할 수 있는 서비스 집합을 제공 합니다. 예를 들어, Visual Studio 서비스를 사용 하면 도구 창을 동적으로 표시 하거나 숨길 수 있으며 도움말, 상태 표시줄 또는 UI 이벤트에 액세스할 수 있습니다. Visual Studio 편집기는 편집기 확장을 통해 가져올 수 있는 서비스도 제공 합니다. 자세한 내용은 [서비스 사용 및 제공](../../extensibility/using-and-providing-services.md)을 참조 하세요.

## <a name="debugger"></a>디버거
 디버거는 언어별 디버깅 구성 요소에 대 한 사용자 인터페이스입니다. 새 언어 서비스를 만든 경우 디버거에 후크 할 특정 디버그 엔진을 만들어야 합니다. 자세한 내용은 [Visual Studio 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)을 참조 하세요.

## <a name="source-control"></a>소스 제어
 소스 제어 플러그 인 또는 VSPackage를 구현 하는 방법에 대 한 자세한 내용은 [원본 제어](../../extensibility/internals/source-control.md)를 참조 하세요.

## <a name="wizards"></a>마법사
 새 프로젝트 형식과 함께 마법사를 만들어 사용자가 해당 형식의 새 프로젝트를 만들 때 적절 한 결정을 내릴 수 있습니다. 자세한 내용은 [마법사](../../extensibility/internals/wizards.md)를 참조 하십시오.

## <a name="custom-tools"></a>사용자 지정 도구
 사용자 지정 도구를 사용 하면 프로젝트의 항목과 도구를 연결 하 고 파일이 저장 될 때마다 해당 도구를 실행할 수 있습니다. 자세한 내용은 [사용자 지정 도구](../../extensibility/internals/custom-tools.md)를 참조 하세요.

## <a name="vssdk-utilities"></a>VSSDK 유틸리티
 Vspackage의 다양 한 측면에서 작업 하기 위해 필요할 수 있는 유틸리티 집합이 포함 되어 있습니다. 자세한 내용은 하 [이 항목을 참조 하세요.](../../extensibility/internals/vssdk-utilities.md)

## <a name="using-windows-installer"></a>Windows Installer 사용
 VSIX 설치 관리자가 아닌 Windows Installer를 사용 해야 하는 경우도 있습니다. 예를 들어 레지스트리에 써야 할 수도 있습니다. 확장과 함께 Windows Installer를 사용 하는 방법에 대 한 자세한 내용은 [Windows Installer를 사용 하 여 Vspackage 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md)를 참조 하세요.

## <a name="help-viewer"></a>도움말 뷰어
 도움말 및 F1 페이지를 도움말 뷰어에 통합할 수 있습니다. 자세한 내용은 [MICROSOFT 도움말 뷰어 SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md)를 참조 하세요.

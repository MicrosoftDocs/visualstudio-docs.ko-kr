---
title: 비주얼 스튜디오 SDK 내부 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707583"
---
# <a name="inside-the-visual-studio-sdk"></a>Visual Studio SDK 기본 사항

이 섹션에서는 Visual Studio 아키텍처, 구성 요소, 서비스, 스키마, 유틸리티 등을 비롯한 Visual Studio 확장에 대한 자세한 정보를 제공합니다.

## <a name="extensibility-architecture"></a>확장성 아키텍처
 다음 그림에서는 Visual Studio 확장성 아키텍처를 보여 주며 있습니다. VSPackage는 IDE에서 서비스로 공유되는 응용 프로그램 기능을 제공합니다. 또한 표준 IDE는 IDE 창 기능에 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>대한 액세스를 제공하는 "와 같은 광범위한 서비스를 제공합니다.

 ![환경 아키텍처 그래픽](../../extensibility/internals/media/environment.gif "환경") 비주얼 스튜디오 아키텍처의 일반화 된 보기

## <a name="vspackages"></a>VSPackages
 VSPackage는 UI 요소, 서비스, 프로젝트, 편집기 및 디자이너를 사용하여 Visual Studio를 구성 및 확장하는 소프트웨어 모듈입니다. VS패키지는 비주얼 스튜디오의 중앙 아키텍처 단위입니다. 자세한 내용은 [VSPackages](../../extensibility/internals/vspackages.md)을 참조하세요.

## <a name="visual-studio-shell"></a>Visual Studio Shell
 Visual Studio 셸은 기본 기능을 제공하고 구성 요소 VSPackage 및 MEF 확장 간의 상호 통신을 지원합니다. 자세한 내용은 [Visual Studio 셸](../../extensibility/internals/visual-studio-shell.md)을 참조하십시오.

## <a name="user-experience-guidelines"></a>사용자 환경 지침
 Visual Studio용 의 새로운 기능을 디자인하려는 경우 디자인 및 유용성 팁인 [Visual Studio 사용자 환경 지침에](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)대한 다음 지침을 살펴봐야 합니다.

## <a name="commands"></a>명령
 명령은 문서 인쇄, 보기 새로 고침 또는 새 파일 만들기 등의 작업을 수행하는 함수입니다.

 Visual Studio를 확장할 때 명령을 만들고 Visual Studio 셸에 등록할 수 있습니다. 이러한 명령이 IDE에 표시되는 방법을 지정할 수 있습니다(예: 메뉴 또는 도구 모음). 일반적으로 **도구** 메뉴에 사용자 지정 명령이 나타나고 도구 창을 표시하는 명령이 **보기** 메뉴의 **다른 Windows** 하위 메뉴에 나타납니다.

 명령을 만들 때 명령어에 대한 이벤트 처리기도 만들어야 합니다. 이벤트 처리기는 명령이 표시되거나 활성화되는 시기를 결정하고, 해당 텍스트를 수정할 수 있으며, 명령이 활성화될 때 적절하게 응답되도록 합니다. 대부분의 경우 IDE는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스를 사용하여 명령을 처리합니다. Visual Studio의 명령은 로컬 선택에 따라 가장 안쪽의 명령 컨텍스트로 시작하여 전역 선택에 따라 가장 바깥쪽 컨텍스트로 진행됩니다. 주 메뉴에 추가된 명령은 즉시 스크립팅에 사용할 수 있습니다.

 자세한 내용은 [명령, 메뉴 및 도구 모음을](../../extensibility/internals/commands-menus-and-toolbars.md)참조하십시오.

## <a name="menus-and-toolbars"></a>메뉴 및 도구 모음
 메뉴와 도구 모음은 사용자가 명령을 호출하는 방법을 제공합니다. 메뉴는 일반적으로 도구 창 맨 위에 개별 텍스트 항목으로 표시되는 명령의 행 또는 열입니다. 하위 메뉴는 사용자가 작은 화살표가 포함된 명령을 클릭할 때 나타나는 보조 메뉴입니다. 컨텍스트 메뉴는 사용자가 특정 UI 요소를 마우스 오른쪽 단추로 클릭할 때 나타납니다. 일부 일반적인 메뉴 이름은 **파일,** **편집,** **보기**및 **창**입니다. 자세한 내용은 [메뉴 및 명령 확장을](../../extensibility/extending-menus-and-commands.md)참조하십시오.

 도구 모음은 단추의 행 또는 열이며 콤보 상자, 목록 상자 및 텍스트 상자와 같은 기타 컨트롤입니다. 도구 모음 단추에는 일반적으로 **파일 열기** 명령의 폴더 아이콘또는 **인쇄** 명령을 위한 프린터와 같은 아이콘 이미지가 있습니다. 모든 도구 모음 요소는 명령과 연결됩니다. 도구 모음 단추를 클릭하면 관련 명령이 실행됩니다. 드롭다운 컨트롤의 경우 드롭다운 목록의 각 항목은 다른 명령과 연결됩니다. 스플리터 컨트롤과 같은 일부 도구 모음 컨트롤은 하이브리드입니다. 컨트롤의 한쪽은 도구 모음 단추이고 다른 쪽은 클릭할 때 여러 명령을 표시하는 아래쪽 화살표입니다.

## <a name="tool-windows"></a>도구 창
 도구 창은 IDE에서 정보를 표시하는 데 사용됩니다. **도구 상자**, **솔루션 탐색기**, **속성** 창 및 **웹 브라우저는** 도구 창의 예입니다.

 도구 창은 일반적으로 사용자가 상호 작용할 수 있는 다양한 컨트롤을 제공합니다. 예를 들어 **속성** 창을 사용하면 사용자가 특정 용도에 적합한 개체의 속성을 설정할 수 있습니다. **속성** 창은 이러한 의미에서 전문화 되어 있지만 다양 한 다른 상황에서 사용할 수 있기 때문에 또한 일반적인. 마찬가지로 **출력** 창은 텍스트 기반 출력을 제공하지만 Visual Studio의 많은 하위 시스템이 Visual Studio 사용자에게 출력을 제공하는 데 사용할 수 있기 때문에 특수합니다.

 여러 도구 창이 포함된 Visual Studio의 다음 그림을 고려하십시오.

 ![스크린샷](../../extensibility/internals/media/t1gui.png "T1gui")

 일부 도구 창은 솔루션 탐색기 도구 창을 표시하고 다른 도구 창을 숨기지만 탭을 클릭하여 사용할 수 있도록 하는 단일 창에 함께 도킹됩니다. 그림은 하나의 창에 함께 도킹된 두 개의 다른 도구 창인 **오류 목록** 및 **출력** 창을 보여 주며 있습니다.

 또한 여러 편집기 창을 보여 주 문서 창이 표시됩니다. 도구 창에는 일반적으로 하나의 인스턴스(예: **하나의 솔루션 탐색기만**열 수 있음)가 있지만, 편집기 창에는 여러 인스턴스가 있을 수 있으며, 각 인스턴스는 별도의 문서를 편집하는 데 사용되지만 모두 동일한 창에 도킹됩니다. 그림에는 두 개의 편집기 창, 하나의 양식 디자이너 창이 있는 문서 창이 표시됩니다. 문서 창의 모든 창을 클릭하여 탭을 사용할 수 있지만 파일이 포함된 편집기 창은 EditorPane.cs 활성화되어 있습니다.

 Visual Studio를 확장하면 Visual Studio 사용자가 확장과 상호 작용할 수 있는 도구 창을 만들 수 있습니다. Visual Studio 사용자가 문서를 편집할 수 있도록 고유한 편집기도 만들 수 있습니다. 도구 창과 편집기는 Visual Studio에 통합되므로 도킹하거나 탭에 올바르게 표시하도록 프로그래밍할 필요가 없습니다. Visual Studio에 올바르게 등록되면 Visual Studio에서 도구 창 및 문서 창의 일반적인 기능이 자동으로 갖습니다. 자세한 내용은 [도구 확장 및 사용자 지정 을](../../extensibility/extending-and-customizing-tool-windows.md)참조하십시오.

## <a name="document-windows"></a>문서 창
 문서 창은 MDI(다중 문서 인터페이스) 창의 프레임자 창입니다. 문서 창은 일반적으로 텍스트 편집기, 양식 편집기(디자이너라고도 함) 또는 편집 컨트롤을 호스트하는 데 사용되지만 다른 기능 형식을 호스트할 수도 있습니다. **새 파일** 대화 상자에는 Visual Studio에서 제공하는 문서 창의 예가 포함되어 있습니다.

 대부분의 편집자는 프로그래밍 언어 또는 HTML 페이지, 프레임 세트, C++ 파일 또는 헤더 파일과 같은 파일 형식에 만전을 기합니다. **새 파일** 대화 상자에서 템플릿을 선택하면 사용자는 템플릿과 연결된 파일 형식에 대한 편집기의 문서 창을 동적으로 만듭니다. 사용자가 기존 파일을 열 때 문서 창도 만들어집니다.

 문서 창은 MDI 클라이언트 영역으로 제한됩니다. 각 문서 창에는 상단에 탭이 있으며 탭 순서는 MDI 영역에서 열릴 수 있는 다른 창에 연결됩니다. 문서 창의 탭을 마우스 오른쪽 단추로 클릭하면 MDI 영역을 여러 가로 또는 세로 탭 그룹으로 분할하는 옵션이 포함된 바로 가기 메뉴가 표시됩니다. MDI 영역을 분할하면 여러 파일을 동시에 볼 수 있습니다. 자세한 내용은 [문서 창](../../extensibility/internals/document-windows.md)을 참조하십시오.

## <a name="editors"></a>편집기
 Visual Studio 편집기를 사용하면 MEF(관리되는 확장성 프레임워크)를 통해 사용자 지정하고 사용자 고유의 콘텐츠 유형에 사용할 수 있습니다. 대부분의 경우 편집기를 확장하기 위해 VSPackage를 만들 필요가 없지만 셸의 피처(예: 메뉴 명령 또는 바로 가기 키)를 포함하려는 경우 MEF 확장을 VSPackage와 결합할 수 있습니다.

 예를 들어 데이터베이스를 읽고 쓰려는 경우 또는 디자이너를 사용하려는 경우와 같은 사용자 지정 편집기를 만들 수도 있습니다. 메모장이나 마이크로소프트 워드패드와 같은 외부 편집기도 사용할 수 있습니다. 자세한 내용은 [편집기 및 언어 서비스 확장을](../../extensibility/editor-and-language-service-extensions.md)참조하십시오.

## <a name="language-services"></a>언어 서비스
 Visual Studio 편집기에서 새 프로그래밍 키워드 또는 새 프로그래밍 언어를 지원하려면 언어 서비스를 만듭니다. 각 언어 서비스는 특정 편집기 기능을 완전히, 부분적으로 또는 전혀 구현할 수 없습니다. 언어 서비스는 구성 방법에 따라 구문 강조 표시, 중괄호 일치, IntelliSense 지원 및 편집기의 기타 기능을 제공할 수 있습니다.

 언어 서비스의 중심에는 파서와 스캐너가 있습니다. 스캐너(또는 lexer)는 소스 파일을 토큰이라고 하는 요소로 나누고 파서는 이러한 토큰 간의 관계를 설정합니다. 언어 서비스를 만들 때 Visual Studio에서 언어의 토큰과 문법을 이해할 수 있도록 파서와 스캐너를 구현해야 합니다. 관리되는 언어 또는 관리되지 않는 언어 서비스를 만들 수 있습니다. 자세한 내용은 [레거시 언어 서비스 확장성](../../extensibility/internals/legacy-language-service-extensibility.md)을 참조하십시오.

## <a name="projects"></a>프로젝트

Visual Studio에서 프로젝트는 개발자가 소스 코드 및 기타 리소스를 구성하고 빌드하는 데 사용하는 컨테이너입니다. 프로젝트를 통해 소스 코드, 웹 서비스 및 데이터베이스에 대한 참조 및 기타 리소스를 구성, 빌드, 디버깅 및 배포할 수 있습니다. VSPackage는 프로젝트 유형, 프로젝트 하위 유형 및 사용자 지정 도구를 제공하여 Visual Studio 프로젝트 시스템을 확장할 수 있습니다.

응용 프로그램을 만들기 위해 함께 작동하는 하나 이상의 프로젝트를 그룹화하는 *솔루션에서*프로젝트를 함께 수집할 수도 있습니다. 솔루션과 관련된 프로젝트 및 상태 정보는 텍스트 기반 [솔루션(.sln) 파일과](solution-dot-sln-file.md) 이진 솔루션 사용자 [옵션(.suo) 파일에](solution-user-options-dot-suo-file.md)저장됩니다. 이러한 파일은 이전 버전의 Visual Basic에서 사용된 그룹(.vbg) 파일및 이전 버전의 C++에서 사용된 작업 영역(.dsw) 및 사용자 옵션(.opt) 파일과 유사합니다.

자세한 내용은 [프로젝트](../../extensibility/internals/projects.md) 및 [솔루션](../../extensibility/internals/solutions-overview.md)을 참조하십시오.

## <a name="project-and-item-templates"></a>프로젝트 및 항목 템플릿
 Visual Studio에는 미리 정의된 프로젝트 템플릿과 프로젝트 항목 템플릿이 포함됩니다. 사용자 고유의 템플릿을 만들거나 커뮤니티에서 템플릿을 획득한 다음 Visual Studio에 통합할 수도 있습니다. [MSDN 코드 갤러리는](https://code.msdn.microsoft.com/site/search?query=visual%20studio) 템플릿 및 확장을 위해 이동하는 곳입니다.

 템플릿에는 특정 종류의 응용 프로그램, 제어, 라이브러리 또는 클래스를 빌드하는 데 필요한 프로젝트 구조 및 기본 파일이 포함되어 있습니다. 템플릿 중 하나와 유사한 소프트웨어를 개발하려는 경우 템플릿을 기반으로 하는 프로젝트를 만든 다음 해당 프로젝트의 파일을 수정합니다.

> [!NOTE]
> 이 템플릿 아키텍처는 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 프로젝트에 대해 지원되지 않습니다.

 자세한 내용은 [프로젝트 및 프로젝트 항목 템플릿 추가를](../../extensibility/internals/adding-project-and-project-item-templates.md)참조하십시오.

## <a name="properties-and-options"></a>속성 및 옵션
 **속성** 창에는 선택한 단일 또는 여러 항목의 속성이 표시됩니다: [속성 옵션 확장](../../extensibility/internals/extending-properties.md) 페이지에는 프로그래밍 언어 또는 VSPackage: [옵션 및 옵션 페이지와](../../extensibility/internals/options-and-options-pages.md)같은 특정 구성 요소와 관련된 옵션 집합이 포함되어 있습니다. 설정은 일반적으로 가져오고 내보낼 수 있는 UI 관련 기능입니다: [사용자 설정 에 대한 지원](../../extensibility/internals/support-for-user-settings.md).

## <a name="visual-studio-services"></a>비주얼 스튜디오 서비스
 서비스는 구성 요소가 사용할 특정 인터페이스 집합을 제공합니다. Visual Studio는 확장을 포함하여 모든 구성 요소에서 사용할 수 있는 서비스 집합을 제공합니다. 예를 들어 Visual Studio 서비스를 사용하면 도구 창을 동적으로 표시하거나 숨길 수 있으며 도움말, 상태 표시줄 또는 UI 이벤트에 액세스할 수 있습니다. 또한 Visual Studio 편집기는 편집기 확장에서 가져올 수 있는 서비스도 제공합니다. 자세한 내용은 [서비스 사용 및 제공](../../extensibility/using-and-providing-services.md)을 참조하십시오.

## <a name="debugger"></a>디버거
 디버거는 언어별 디버깅 구성 요소에 대한 사용자 인터페이스입니다. 새 언어 서비스를 만든 경우 디버거에 연결할 특정 디버그 엔진을 만들어야 합니다. 자세한 내용은 [Visual Studio 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)을 참조하십시오.

## <a name="source-control"></a>소스 제어
 소스 제어 플러그인 또는 VSPackage 구현에 대한 자세한 내용은 [소스 제어](../../extensibility/internals/source-control.md)을 참조하십시오.

## <a name="wizards"></a>마법사
 마법사가 해당 유형의 새 프로젝트를 만들 때 사용자가 올바른 결정을 내릴 수 있도록 마법사를 새 프로젝트 유형과 함께 만들 수 있습니다. 자세한 내용은 [마법사 를](../../extensibility/internals/wizards.md)참조하십시오.

## <a name="custom-tools"></a>사용자 지정 도구
 사용자 지정 도구를 사용하면 도구를 프로젝트의 항목과 연결하고 파일이 저장될 때마다 해당 도구를 실행할 수 있습니다. 자세한 내용은 [사용자 지정 도구를](../../extensibility/internals/custom-tools.md)참조하십시오.

## <a name="vssdk-utilities"></a>VSSDK 유틸리티
 VSSDK에는 VSPackage의 다양한 측면을 사용하는 데 필요한 유틸리티 집합이 포함되어 있습니다. 자세한 내용은 [VSSDK 유틸리티](../../extensibility/internals/vssdk-utilities.md)를 참조하십시오.

## <a name="using-windows-installer"></a>Windows 설치 관리자 사용
 VSIX 설치 관리자 대신 Windows 설치 관리자를 사용해야 하는 경우도 있습니다. 확장 과 함께 Windows 설치 관리자를 사용하는 것에 대한 자세한 내용은 [WINDOWS 설치 관리자를 사용하여 VS패키지 설치를](../../extensibility/internals/installing-vspackages-with-windows-installer.md)참조하십시오.

## <a name="help-viewer"></a>도움말 뷰어
 사용자 고유의 도움말 및 F1 페이지를 도움말 뷰어에 통합할 수 있습니다. 자세한 내용은 [Microsoft 도움말 뷰어 SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md)를 참조하십시오.

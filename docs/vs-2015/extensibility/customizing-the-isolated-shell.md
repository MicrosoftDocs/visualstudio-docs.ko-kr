---
title: 격리 셸 사용자 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 724d4d0c4b392a362e702f33ea996df3a6fc0ad6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555971"
---
# <a name="customizing-the-isolated-shell"></a>격리 셸 사용자 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 사용자 인터페이스의 여러 측면을 변경 하 고 특수 응용 프로그램에 포함 된 명령과 기능을 제한 하 여 Visual Studio 격리 셸 응용 프로그램을 사용자 지정할 수 있습니다.  
  
## <a name="using-the-applicationpkgdef-file"></a>.Pkgdef 파일 사용  
 격리 셸 템플릿 솔루션에는 *SolutionName*포함 되어 있습니다. .Pkgdef 파일을 사용 하 여 다음 기능을 수정할 수 있습니다.  
  
##### <a name="the-application-title"></a>응용 프로그램 제목  
 *SolutionName*에서 "AppName" 행의 값을 변경 하 여 응용 프로그램의 제목 표시줄에 표시 되는 이름인 응용 프로그램 제목을 사용자 지정할 수 있습니다. .Pkgdef 파일입니다. 자세한 내용은 [연습: 기본 격리 셸 응용 프로그램 만들기](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)를 참조 하세요.  
  
 응용 프로그램 제목에 현재 로드 된 프로젝트를 표시 하지 않으려면 *SolutionName*에서 "ShowHierarchyRootInTitle" 행의 값을 변경 합니다. Dword: 00000001에서 dword: 00000000 .pkgdef 파일입니다.  
  
##### <a name="the-application-icon"></a>응용 프로그램 아이콘  
 응용 프로그램 제목 표시줄에서 응용 프로그램 이름에 표시 되는 아이콘인 응용 프로그램 아이콘을 사용자 지정할 수 있습니다. 다른 아이콘을 아이콘 디렉터리에 복사 합니다. **솔루션 탐색기**에서 리소스 파일 폴더에 아이콘을 추가 합니다. 그런 다음 VSShellStub .rc 파일을 열고 IDI_STUBPROGRAM의 값을 새 아이콘의 이름으로 바꿉니다. 자세한 내용은 [연습: 기본 격리 셸 응용 프로그램 만들기](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)를 참조 하세요.  
  
##### <a name="the-command-line-logo"></a>명령줄 로고  
 *SolutionName*에서 "CommandLineLogo" 행의 값을 변경 하 여 명령줄에서 응용 프로그램을 시작할 때 표시 되는 텍스트인 명령줄 로고를 사용자 지정할 수 있습니다. .Pkgdef 파일입니다. 자세한 내용은 [연습: 기본 격리 셸 응용 프로그램 만들기](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md) 를 참조 하세요.  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>사용자 파일 하위 폴더의 이름입니다.  
 *SolutionName*에서 "UserFilesSubFolderName" 행의 값을 변경 하 여 응용 프로그램이 사용자 파일에 대해 유지 관리 하는 폴더의 이름을 변경할 수 있습니다. .Pkgdef 파일입니다.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>새 프로젝트 대화 상자의 솔루션 트리 노드 제목  
 *SolutionName*에서 "NewProjDlgSlnTreeNodeTitle" 행의 값을 변경 하 여 새 프로젝트 대화 상자에서 솔루션 노드의 제목을 사용자 지정할 수 있습니다. .Pkgdef 파일입니다.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>새 프로젝트 대화 상자의 설치 된 템플릿 헤더  
 *SolutionName*에 있는 "NewProjDlgInstalledTemplatesHdr" 행의 값을 변경 하 여 새 프로젝트 대화 상자에서 설치 된 템플릿 헤더를 변경할 수 있습니다. .Pkgdef 파일입니다.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>기본적으로 기타 파일을 숨길지 여부  
 *SolutionName*에서 "HideMiscellaneousFilesByDefault" 행의 값을 변경 하 여 기본적으로 기타 파일을 숨길지 여부를 지정할 수 있습니다. .Pkgdef 파일입니다. 기타 파일을 숨기려면 값을 설정 하 `dword:00000001` 고 파일을 표시 하려면 값을 설정 `dword:00000000` 합니다.  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>출력 창을 사용 하지 않도록 설정할지 여부  
 *SolutionName*에서 "DisableOutputWindow" 행의 값을 변경 하 여 응용 프로그램에서 출력 창을 사용 하지 않도록 설정할지 여부를 지정할 수 있습니다. .Pkgdef 파일입니다. 출력 창을 사용 하지 않도록 설정 하려면 값을 설정 하 `dword:00000001` 고 출력 창을 표시 하려면 값을 설정 `dword:00000000` 합니다.  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>주 창에서 삭제 된 파일을 허용할지 여부  
 *SolutionName*에서 "AllowsDroppedFilesOnMainWindow" 행의 값을 변경 하 여 응용 프로그램의 주 창에서 삭제 된 파일을 허용할지 여부를 지정할 수 있습니다. .Pkgdef 파일입니다. 삭제 된 파일을 허용 하려면 값을 설정 하 `dword:00000001` 고 삭제 된 파일을 허용 하지 않으려면 값을 설정 `dword:00000000` 합니다.  
  
##### <a name="the-default-search-page"></a>기본 검색 페이지  
 *SolutionName*에서 "DefaultSearchPage" 행의 값을 변경 하 여 웹 브라우저 창을 열 때 표시 되는 페이지인 웹 브라우저 페이지를 사용자 지정할 수 있습니다. .Pkgdef 파일입니다.  
  
##### <a name="the-default-home-page"></a>기본 홈 페이지  
 *SolutionName*에서 "Defaul% mepage" 행의 값을 변경 하 여 홈 페이지를 사용자 지정할 수 있습니다. .Pkgdef 파일입니다. 자세한 내용은 [연습: 기본 격리 셸 응용 프로그램 만들기](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md) 를 참조 하세요.  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>솔루션 개념을 숨길지 여부  
 *SolutionName*에서 "HideSolutionConcept" 행의 값을 변경 하 여 응용 프로그램에서 솔루션을 숨길지 여부를 지정할 수 있습니다. .Pkgdef 파일입니다. 솔루션을 숨기려면 값을 설정 하 `dword:00000001` 고 솔루션을 표시 하려면 값을 설정 `dword:00000000` 합니다.  
  
##### <a name="the-default-debug-engine"></a>기본 디버그 엔진  
 *SolutionName*에서 "DefaultDebugEngine" 행의 값을 변경 하 여 응용 프로그램에서 사용 하는 디버그 엔진을 변경할 수 있습니다. 디버그 엔진의 GUID에 .pkgdef 파일을 적용 합니다.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>사용자 옵션 파일의 파일 확장명입니다.  
 *SolutionName*에서 "UserOptsFileExt" 행의 값을 변경 하 여 응용 프로그램이 사용자 파일에 대해 유지 관리 하는 폴더의 이름을 변경할 수 있습니다. .Pkgdef 파일입니다.  
  
##### <a name="the-solution-file-extension"></a>솔루션 파일 확장명  
 *SolutionName*에서 "Solution fileext" 행의 값을 변경 하 여 솔루션 파일에 사용 되는 확장을 변경할 수 있습니다. .Pkgdef 파일입니다.  
  
##### <a name="the-default-user-files-folder-root"></a>기본 사용자 파일 폴더 루트  
 *SolutionName*에서 "UserFilesSubFolderName" 행의 값을 변경 하 여 응용 프로그램에 대 한 사용자 파일의 루트 폴더 이름을 변경할 수 있습니다. .Pkgdef 파일입니다.  
  
##### <a name="the-solution-file-creator-identifier"></a>솔루션 파일 작성자 식별자  
 *SolutionName*에서 "SolutionFileCreatorIdentifier" 행의 값을 변경 하 여 솔루션 파일에 사용 되는 식별자를 변경할 수 있습니다. .Pkgdef 파일입니다.  
  
##### <a name="the-default-projects-location"></a>기본 프로젝트 위치  
 *SolutionName*에서 "DefaultProjectsLocation" 행의 값을 변경 하 여 기본 프로젝트 위치의 이름을 변경할 수 있습니다. .Pkgdef 파일입니다.  
  
##### <a name="the-application-localization-package"></a>응용 프로그램 지역화 패키지  
 *SolutionName*에서 "AppLocalizationPackage" 행의 값을 변경 하 여 응용 프로그램에 사용 되는 지역화 패키지를 변경할 수 있습니다. .Pkgdef 파일입니다.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>제목에 계층 루트를 표시할지 여부  
 *SolutionName*에서 "ShowHierarchyRootInTitle" 행의 값을 변경 하 여 응용 프로그램의 제목 표시줄에 계층 루트를 표시할지 여부를 지정할 수 있습니다. .Pkgdef 파일입니다. 계층 루트를 표시 하려면 값을 설정 하 `dword:00000001` 고 계층 루트를 숨기려면 값을 설정 `dword:00000000` 합니다.  
  
##### <a name="specifying-a-start-page"></a>시작 페이지 지정  
 *SolutionName*에서 사용자 지정 응용 프로그램에 대 한 시작 페이지를 지정 합니다. .Pkgdef 파일을 열고, "DisableStartPage" 값을로 설정 하 `dword:00000000` 고, `[$RootKey$\StartPage\Default]` URI를 .xaml 파일의 위치로 설정 합니다.  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 *SolutionName*UI 프로젝트의 applicationcommands 파일에서 "No_ShellPkg_startPageCommand" 항목을 주석으로 처리 합니다.  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 .Xaml 파일 및 필요한 모든 그래픽 파일을 *SolutionName* 프로젝트에 추가 해야 합니다. 이러한 파일은 실제로는 다른 디렉터리에서 추가 되지 않고 *SolutionName* 프로젝트 디렉터리에 복사 해야 합니다.  
  
 모든 파일에서 파일을 *$RootFolder $* 디렉터리에 복사 하려면 **항목 유형** 속성을 **격리 된 셸 파일** 로 설정 합니다. **항목 유형** 속성을 설정 하려면 파일을 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다. 이 속성은 **구성 속성**, **일반**에서 찾을 수 있습니다.  
  
 시작 페이지를 사용자 지정 하는 방법에 대 한 자세한 내용은 [시작 페이지 사용자 지정](../ide/customizing-the-start-page-for-visual-studio.md)을 참조 하세요.  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>격리 된 셸의 다른 요소 사용  
 격리 셸 솔루션 템플릿에 포함 된 다른 파일 및 프로젝트를 사용 하 여 응용 프로그램을 추가로 사용자 지정할 수 있습니다.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Visual Studio 패키지 사용/사용 안 함  
 *SolutionName*.pkgundef 파일을 사용 하면 특정 패키지를 제외 하 고 특정 종류의 Visual Studio 기능을 사용 하지 않도록 설정할 수 있습니다. 예를 들어 다음 줄은 다음과 같습니다.  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 **새 프로젝트** 대화 상자에 표시 되는 프로젝트 템플릿 집합에서 기타 파일 프로젝트를 제거 합니다. 자세한 내용은 [연습: 기본 격리 셸 응용 프로그램 만들기](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)를 참조 하세요.  
  
##### <a name="enabledisable-menu-commands"></a>메뉴 명령 사용/사용 안 함  
 *SolutionName*파일에는 격리 된 셸에서 사용할 수 있는 모든 메뉴 명령의 주석 처리 된 목록이 포함 되어 있습니다. 지정 된 명령을 사용 하지 않도록 설정 하려면 해당 행의 주석 처리를 제거 합니다. 예를 들어 창/분할 주석을 사용 하지 않도록 설정 하려면 행의 주석 처리를 제거 `<Define name="No_SplitCommand"/>` 합니다. 자세한 내용은 [연습: 기본 격리 셸 응용 프로그램 만들기](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)를 참조 하세요.  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>시작 화면에 사용 되는 비트맵입니다.  
 시작 화면에 사용 되는 비트맵을 사용자 지정할 수 있습니다 .이는 응용 프로그램이 시작 될 때 표시 되는 창인 *SolutionName*의 "SplashScreenBitmap" 행의 값을 변경 하는 것입니다. .Pkgdef 파일입니다. 자세한 내용은 [연습: 기본 격리 셸 응용 프로그램 만들기](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)를 참조 하세요.  
  
##### <a name="the-helpabout-window"></a>도움말/정보 창  
 격리 셸 템플릿에서는 응용 프로그램에 대 한 도움말/정보 상자를 사용자 지정 하는 데 사용할 수 있는 별도의 프로젝트가 있습니다. 자세한 내용은 [연습: 기본 격리 셸 응용 프로그램 만들기](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)를 참조 하세요.

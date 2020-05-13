---
title: 비주얼 스튜디오 도구 모음의 GUID 및 ID | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe42821cdacc038d767e52373d45ddd7b8954323
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708221"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>비주얼 스튜디오 도구 모음의 GUID 및 아이디
이 항목에서는 Visual Studio 통합 개발 환경(IDE)에 포함된 도구 모음의 GUID 및 ID 값과 해당 도구에 포함된 그룹의 GUID 및 ID 값을 참조합니다. 이러한 값은 Visual Studio SDK의 일부로 설치된 *.vsct* 파일에 정의됩니다. 자세한 내용은 [IDE 정의 명령, 메뉴 및 그룹을](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)참조하십시오.

> [!NOTE]
> Visual Studio에서 사용할 수 있는 많은 도구 모음은 Visual Studio에서 정의하지 않으며 GUID 및 ID 값은 공개되지 않습니다. 이 항목에서는 Visual Studio SDK *.vsct* 파일에 정의된 도구 모음만 나열합니다.

 *.vsct* 파일에 정의된 IDE 개체로 작업하는 방법에 대한 자세한 내용은 [메뉴 및 명령 확장](../../extensibility/extending-menus-and-commands.md)을 참조하십시오.

 Visual Studio IDE에서 제공하는 기본 도구 `guidSHLMainMenu`모음은 구문을 사용하여 `GUID:ID` 달리 지정된 경우를 제외하고 GUID를 사용합니다.

## <a name="ide-toolbars"></a>IDE 도구 모음
 다음 도구 모음은 Visual Studio IDE에서 제공합니다. 도구 모음 메뉴의 도구 모음 하위 메뉴에서 도구를 선택하여 도구 **모음을** 표시할 수 **있습니다.** 도구 창의 도구 모음은 이 섹션에 포함되지 않습니다.

 그룹만 도구 모음에서 직접 내려갈 수 있습니다. 그룹을 추가하려면 도구를 도구 모음의 GUID 및 ID에 부모를 설정합니다. 도구 모음에 단추를 추가하려면 도구를 도구 모음의 그룹으로 설정합니다.

|도구 모음|ID|
|-------------|--------|
|Standard|IDM_VS_TOOL_STANDARD|
|빌드|IDM_VS_TOOL_BUILD|
|텍스트 편집기|IDM_VS_TOOL_TEXTEDITOR|
|디버그|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|
|디버그 위치|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|

### <a name="special-toolbars"></a>특수 도구 모음
 이러한 도구 모음은 Visual Studio IDE에 의해 정의되지만 특수 기능을 제공하고 명령 그룹을 호스팅하지 않습니다.

|도구 모음|ID|
|-------------|--------|
|Add 명령|IDM_VS_TOOL_ADDCOMMAND|
|정의되지 않음|IDM_VS_TOOL_UNDEFINED|
|XML 스키마|IDM_VS_TOOL_SCHEMA|
|XML 데이터|IDM_VS_TOOL_DATA|

## <a name="groups-on-the-ide-toolbars"></a>IDE 도구 모음의 그룹
 표준 도구 모음에 단추를 추가하려면 다음 그룹 중 하나를 부모로 설정합니다. 그룹은 상위 도구 모음별로 정렬됩니다.

### <a name="standard-toolbar-groups"></a>표준 도구 모음 그룹

|이름|ID|
|----------|--------|
|저장/열기|IDG_VS_TOOLSB_SAVEOPEN|
|잘라내기/복사|IDG_VS_TOOLSB_CUTCOPY|
|실행 취소/다시 실행|IDG_VS_TOOLSB_UNDOREDO|
|실행/빌드|IDG_VS_TOOLSB_RUNBUILD|
|검색|IDG_VS_TOOLSB_SEARCH|
|Windows|IDG_VS_TOOLSB_WINDOWS|
|새 창|IDG_VS_TOOLSB_NEWWINDOWS|
|로드/저장|IDG_VS_WINDOWUI_LOADSAVE|
|계기|IDG_VS_TOOLSB_GAUGE|

### <a name="build-toolbar-groups"></a>도구 모음 그룹 빌드

|이름|ID|
|----------|--------|
|빌드 막대|IDG_VS_BUILDBAR|
|취소|IDG_VS_BUILD_CANCEL|

### <a name="text-editor-toolbar-groups"></a>텍스트 편집기 도구 모음 그룹

|이름|ID|
|----------|--------|
|Completion|IDM_VS_TOOL_TEXTEDITOR|
|들여쓰기|IDG_VS_EDITTOOLBAR_INDENT|
|주석|IDG_VS_EDITTOOLBAR_COMMENT|
|책갈피|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|

### <a name="debug-toolbar-groups"></a>디버그 도구 모음 그룹

|이름|ID|
|----------|--------|
|실행|IDM_DEBUG_TOOLBAR|
|단계별 실행|IDG_DEBUG_TOOLBAR_STEPPING|
|조사식|IDG_DEBUG_TOOLBAR_WATCH|
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|

### <a name="debug-location-toolbar-groups"></a>위치 도구 모음 그룹 디버그

|이름|ID|
|----------|--------|
|디버그 위치|IDG_DEBUG_CONTEXT_TOOLBAR|

## <a name="tool-window-toolbars"></a>도구 창 도구 모음
 도구 모음은 IDE 또는 **솔루션 탐색기와**같은 도구 창에 직접 나타날 수 있습니다. 도구 창은 *.vsct* 파일에 정의되어 있지 않으므로 도구 창 도구 모음에는 부모가 정의되어 있지 않습니다. 대신 코드에 배치됩니다. 다음 표에서는 IDE의 도구 창에 나타나는 도구 모음과 도구 모음에 포함된 명령 그룹을 보여 줄 수 있습니다.

> [!NOTE]
> 도구 모음 및 그룹은 `guidSHLMainMenu`GUID:ID 구문을 사용하여 달리 지정된 경우를 제외하고 GUID를 사용합니다. 도구 모음에 GUID를 지정하면 해당 도구 모음에서 후손하는 그룹에도 적용됩니다.

|공구 창|도구 모음|그룹|
|-----------------|-------------|------------|
|솔루션 탐색기|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1.. 5|
|서버 탐색기|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|
|속성|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|
|클래스 뷰|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|
|클래스 뷰|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|
|개체 브라우저|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|
|개체 브라우저|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|
|출력|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|
|찾기 및 바꾸기|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|
|결과 찾기 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|
|결과 찾기 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|
|코드 조각|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|
|책갈피|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|
|작업 목록|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|
|사용자 작업|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|
|오류 목록|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|
|호출 브라우저|IDM_VS_TOOL_CALLBROWSER1.. 16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|
|중단점|guidVS디버그그룹:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|
|디스어셈블리|guidVS디버그그룹:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|
|메모리 1-4|guidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1... 4|IDG_MEMORY_EXPRESSION1.. 4<br /><br /> IDG_MEMORY_COLUMNS1. 4|
|프로세스|guidVS디버그그룹:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|

## <a name="see-also"></a>참조
- [도구 모음에 메뉴 컨트롤러 추가](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)
- [도구 창에 도구 모음 추가](../../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [비주얼 스튜디오 메뉴의 GUID 및 아이디](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

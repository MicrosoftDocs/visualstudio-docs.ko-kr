---
title: 옵션 페이지, 환경, 노드 속성 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio], controlling Tools Options
- Tools Options settings, Environment node properties
ms.assetid: 26dca41f-91fc-4ca7-9103-3da402baa1d5
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b45716db44dcc316ec60604aa0411e6498797ae0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595022"
---
# <a name="options-page-environment-node-properties"></a>옵션 페이지, 환경 노드 속성
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 문서에서는 **옵션** 대화 상자의 **환경** 범주, `DTE.Properties("Environment", <Property Page>)`와 연관된 일부 페이지(또는 속성 컬렉션)에 대해 설명합니다. 각 하위 단원의 제목은 속성 컬렉션에 액세스하는 데 사용되는 호출이며, 각 하위 단원의 표에는 컬렉션의 속성이 나열되어 있습니다.

## <a name="general"></a>일반
 `DTE.Properties("Environment", "General")`

|속성 항목 이름|값|설명|
|------------------------|-----------|-----------------|
|ShowStatusBar|Get/Set (Boolean)|상태 표시줄이 표시되는지 여부를 확인합니다.|
|WindowMenuContainsNItems|Get/Set(Short)|문서 창이 Windows 메뉴 맨 아래에 포함되는 방식을 결정합니다.|
|MRUListContainsNItems|Get/Set(Short)|다수의 파일이 "가장 최근에 사용됨" 하위 메뉴에 표시되는 방식을 결정합니다.|
|애니메이션|Get/Set (Boolean)|IDE(통합 개발 환경)의 상태 표시줄에서 애니메이션을 사용하는지 여부를 결정합니다.|
|AnimationSpeed|Get/Set(Short)||
|AutoAdjustExperience|Get/Set (Boolean)|클라이언트 성능에 따라 시각적 환경을 자동으로 조정합니다.|
|RichClientExperienceOptions|Get/Set(Enum)|<xref:EnvDTE100.vsRichClientExperienceOptions>의 값을 통해 리치 클라이언트 시각적 효과를 사용합니다.|
|CloseButtonActiveTabOnly|Get/Set (Boolean)|**닫기** 단추가 활성 탭에서만 표시되는지 여부를 결정합니다.|
|AutohidePinActiveTabOnly|Get/Set (Boolean)|**자동 숨기기** 단추가 활성 탭에서만 표시되는지 여부를 결정합니다.|

## <a name="add-inmacros-security"></a>추가 기능/매크로 보안
 `DTE.Properties("Environment", "AddinMacrosSecurity")`

|속성 항목 이름|값|설명|
|------------------------|-----------|-----------------|
|MacrosEnabled|Get/Set (Boolean)|매크로를 실행할 수 있습니다.|
|AddinsEnabled|Get/Set (Boolean)|추가 기능을 로드할 수 있습니다.|
|LoadAddinsFromTheWeb|Get/Set (Boolean)|추가 기능을 웹의 URL에서 로드할 수 있습니다.|

## <a name="documents"></a>문서
 `DTE.Properties("Environment", "Documents")`

|속성 항목 이름|값|설명|
|------------------------|-----------|-----------------|
|ReuseSavedActiveDocWindow|Get/Set (Boolean)|현재 문서를 저장하는 경우 새 파일을 열면 현재 문서 창이 다시 사용되는지 여부를 결정합니다. `false`로 설정하면 열리는 각 문서에 대해 항상 새 문서 창이 열립니다.|
|DetectFileChangesOutsideIDE|Get/Set (Boolean)|운영 체제가 디스크에서 파일이 수정되었음을 IDE에 알리면 환경이 IDE에서 열려 있는 파일을 자동으로 다시 로드하는지 여부를 결정합니다.|
|AutoloadExternalChanges|Get/Set (Boolean)|열린 문서가 수정되지 않은 경우 열려 있는 문서에 대한 외부 수정 사항이 감지되면 수정된 파일을 자동으로 다시 로드하는지 여부를 결정합니다. 열린 문서가 수정되며 이 속성이 `true`인 경우 IDE에서는 마치 속성이 `false`인 것처럼 메시지를 표시합니다.|
|InitializeOpenFileFromCurrentDocument|Get/Set (Boolean)|<xref:EnvDTE.DTEClass.OpenFile%2A> 명령이 마지막으로 활성 상태였던 문서에서나 파일을 열었던 마지막 위치에서 디렉터리 및 파일 이름의 초기값을 지정하는지 여부를 결정합니다.|
|MiscFilesProjectSavesLastNItems|Get/Set(Short)|기타 파일 프로젝트에 기록되는 파일의 수를 결정합니다. 결과적으로, 다음에 IDE를 사용할 때는 가장 최근에 열어 두었던 항목을 디스크에서 기타 파일로 볼 수 있습니다.|
|ShowMiscFilesProject|Get/Set (Boolean)|기타 파일 프로젝트를 표시하는지 여부를 결정합니다.|
|CheckForConsisentLineEndings|Get/Set (Boolean)|파일 로드 시 줄 끝이 일관적인지 확인합니다.|
|SaveDocsAsUnicodeWhenDataLoss|Get/Set (Boolean)|데이터를 코드 페이지에서 저장할 수 없을 때 유니코드로 문서를 저장합니다.|
|DontShowGlobalUndoChangeLossDialog|Get/Set (Boolean)|전체 실행 취소가 다른 편집된 파일을 수정한다는 점을 알리는 경고를 표시합니다.|
|AllowEditingReadOnlyFiles|Get/Set (Boolean)|읽기 전용 파일의 편집이 허용되지만 저장하려는 시도가 있는 경우 경고가 표시됩니다.|
|DocumentDockPreference|Get/Set(Enum)|<xref:EnvDTE100.vsDocumentDockPreferenceOptions>. 열려 있는 문서를 삽입할 탭 저장소 내의 위치입니다.|

## <a name="extension-manager"></a>확장명 관리자
 `DTE.Properties("Environment", "ExtensionManager")`

|속성 항목 이름|값|설명|
|------------------------|-----------|-----------------|
|EnableAdminExtensions|Get/Set (Boolean)|관리자 자격 증명으로 Visual Studio가 실행될 때 사용자별 확장을 로드합니다. 이 값이 변경된 후에는 Visual Studio를 다시 시작해야 합니다.|
|EnableOnline|Get/Set (Boolean)|Visual Studio 갤러리에 있는 확장에 액세스할 수 있도록 합니다.|
|AutomaticallyCheckForUpdates|Get/Set (Boolean)|설치된 확장에 대한 업데이트를 자동으로 확인합니다.|

## <a name="find-and-replace"></a>찾기 및 바꾸기
 `DTE.Properties("Environment", "FindAndReplace")`

|속성 항목 이름|값|설명|
|------------------------|-----------|-----------------|
|ShowWarningMessages|Get/Set (Boolean)|경고 메시지를 표시합니다.|
|InitializeFromEditor|Get/Set (Boolean)|**찾을 내용** 상자를 편집기의 텍스트로 자동으로 채웁니다.|
|ShowMessageBoxes|Get/Set (Boolean)|정보 메시지를 표시합니다.|
|HideWindowsAfterMatchFromQuickFindReplace|Get/Set (Boolean)|**빠른 찾기** 또는 **빠른 바꾸기**를 사용하여 일치 항목을 찾은 후에는 **찾기 및 바꾸기** 창을 숨깁니다.|

## <a name="import-and-export-settings"></a>설정 가져오기 및 내보내기
 `DTE.Properties("Environment", "Import and Export Settings")`

|속성 항목 이름|값|설명|
|------------------------|-----------|-----------------|
|TrackTeamSettings|Get/Set (Boolean)|파일에 TeamSettingsFile에서 지정된 설정을 사용합니다.|
|TeamSettingsFile|Get/Set(문자열)|팀 설정이 포함된 파일의 이름입니다.|
|AutoSaveFile|Get/Set(문자열)|사용자 설정이 자동으로 저장되는 파일의 이름입니다.|

## <a name="international-settings"></a>국가별 설정
 `DTE.Properties("Environment", "International")`

|속성 항목 이름|값|설명|
|------------------------|-----------|-----------------|
|언어|Get/Set(문자열)|Visual Studio에 대한 현재 언어의 LCID 값입니다.|

## <a name="keyboard"></a>Keyboard
 `DTE.Properties("Environment", "Keyboard")`

|속성 항목 이름|값|Description|
|------------------------|-----------|-----------------|
|구성표|Get/Set(문자열)|기본 제공 스키마, 로드된 .vsk 파일의 전체 경로가 포함된 문자열 또는 .vsk 파일이 로드되지 않은 경우 "(기본값)"이 포함된 문자열을 반환합니다.|

## <a name="projects-and-solution"></a>프로젝트 및 솔루션
 `DTE.Properties("Environment", "ProjectsAndSolution")`

|속성 항목 이름|값|설명|
|------------------------|-----------|-----------------|
|OnRunOrPreview|Get/Set(문자열)|빌드된 프로젝트를 미리 보거나 실행하기 전에 IDE에서 모든 항목을 저장하는지 여부를 결정합니다.|
|ProjectsLocation|Get/Set(문자열)|**프로젝트 추가** 대화 상자가 새 프로젝트를 저장하는 기본 디렉터리를 결정합니다.|
|ShowOutputWindowBeforeBuild|Get/Set (Boolean)|빌드를 시작하면 **출력** 창이 표시되는지 여부를 결정합니다.|
|ShowTaskListAfterBuild|Get/Set (Boolean)|빌드가 완료되면 실패한 빌드 작업이 **작업 목록**을 표시하는지 여부를 결정합니다.|
|TrackFileSelectionInExplorer|Get/Set (Boolean)|현재 항목이 **솔루션 탐색기**에서 추적되는지 여부를 결정합니다.|
|AlwaysShowSolutionNode|Get/Set (Boolean)|솔루션 노드를 표시할지 여부를 결정합니다.|
|OnlySaveStartupProjectsAndDependencies|Get/Set (Boolean)|저장 작업이 시작 프로젝트와 해당 종속 파일로 제한되는지 여부를 결정합니다.|
|ShowAdvancedBuildConfigurations|Get/Set (Boolean)|고급 빌드 구성이 표시되는지 여부를 결정합니다.|
|ConcurrentBuilds|Get/Set(문자열)|발생할 수 있는 병렬 프로젝트 빌드의 최대 개수를 결정합니다.|
|SaveNewProjects|Get/Set (Boolean)|새 프로젝트가 만들어진 후에 자동으로 저장되는지 여부를 결정합니다.|
|PromptForRenameSymbol|Get/Set (Boolean)|파일 이름을 바꿀 때 기호화된 이름 바꾸기에 대한 프롬프트를 사용할지 여부를 지정합니다.|
|OnRunWhenErrors|Get/Set(Enum)|빌드가 오류 없이 완료되는 경우 실행 시 동작을 지정합니다.|
|OnRunWhenOutOfDate|Get/Set(Enum)|프로젝트가 오래된 경우 실행 시 동작을 지정합니다.|
|ProjectTemplatesLocation|Get/Set(문자열)|사용자 프로젝트 템플릿이 포함된 디렉터리입니다.|
|ProjectItemTemplatesLocation|Get/Set(문자열)|사용자 항목 템플릿이 포함된 디렉터리입니다.|
|DefaultBehaviorForStartupProjects|Get/Set(문자열)||
|MSBuildOutputVerbosity|Get/Set(문자열)|빌드 출력의 세부 정보 표시 수준을 지정합니다.|

## <a name="startup"></a>Startup 클래스
 `DTE.Properties("Environment", "Startup")`

|속성 항목 이름|값|설명|
|------------------------|-----------|-----------------|
|OnStartUp|Get/Set(Enum)|<xref:EnvDTE.vsStartUp>에서 시작 시 수행할 작업으로, 값 0부터 5까지 사용됩니다.<br /><br /> -   0: 홈페이지 열기<br />-   1: 마지막으로 로드한 솔루션 로드<br />-   2: **프로젝트 열기** 대화 상자 표시<br />-   3: **새 프로젝트** 대화 상자 표시<br />-   4: 빈 환경 표시<br />-   5: 시작 페이지 표시|
|StartPageRSSUrl|Get/Set(문자열)|시작 시 사용되는 RSS 피드의 URL입니다.|
|StartPageRefreshDownloadedContent|Get/Set (Boolean)|StartPageRefreshInterval에 지정된 간격이 지날 때마다 시작 페이지를 새로 고칩니다.|
|StartPageRefreshInterval|Get/Set(Short)|시작 페이지를 새로 고치는 시간 간격(분)입니다.|

## <a name="tasklist"></a>TaskList
 `DTE.Properties("Environment", "TaskList")`

|속성 항목 이름|값|설명|
|------------------------|-----------|-----------------|
|ConfirmTaskDeletion|Get/Set (Boolean)|**작업 목록**에서 작업을 삭제할 때 확인 상자를 표시하는지 여부를 지정합니다.|
|WarnOnAddingHiddenItem|Get/Set (Boolean)|표시되지 않을 사용자 작업을 추가할 때 경고가 표시되도록 할지 여부를 지정합니다.|
|DontShowFilePaths|Get/Set (Boolean)|작업 목록에 전체 파일 경로를 표시할지 여부를 지정합니다.|
|CommentTokens|SafeArray|주석 토큰 값의 SafeArray를 반환합니다. 각 값에 `Name`(문자열) 및 `Priority`(<xref:EnvDTE.vsTaskPriority>, 높음, 중간 또는 낮음)의 필드가 있습니다.|

## <a name="web-browser"></a>웹 브라우저
 `DTE.Properties("Environment", "WebBrowser")`

|속성 항목 이름|값|설명|
|------------------------|-----------|-----------------|
|HomePage|Get/Set(문자열)|홈페이지 URL을 나타냅니다.|
|SearchPage|Get/Set(문자열)|검색 페이지 URL을 나타냅니다.|
|ViewSourceIn|Get/Set(Enum)|<xref:EnvDTE.vsBrowserViewSource>(소스, 디자인, 외부)입니다.|
|ViewSourceExternalProgram|Get/Set(문자열)|외부 소스 뷰어의 경로입니다.|

## <a name="see-also"></a>관련 항목

- [옵션 설정 제어](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d)
- [옵션 페이지에서 속성 항목의 이름 확인](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)
- [옵션 페이지, 글꼴 및 색 노드 속성](../../ide/reference/options-page-fonts-and-colors-node-properties.md)
- [옵션 페이지, 텍스트 편집기 노드 속성](../../ide/reference/options-page-text-editor-node-properties.md)
- [환경 옵션 대화 상자](../../ide/reference/environment-options-dialog-box.md)

---
title: 명령 별칭
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- aliases, Visual Studio commands
- Visual Studio, commands
- predefined command aliases
- commands, aliases
- Visual Studio commands
- pre-defined command aliases
- command aliases
ms.assetid: de8bb378-8c1c-4087-a9a5-537fa8314c19
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b420644672309371ab61f1499e22d4745c69c569
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596413"
---
# <a name="visual-studio-command-aliases"></a>Visual Studio Command Aliases

명령 별칭을 통해 명령을 실행하려는 경우 더 적은 문자를 입력할 수 있습니다. **찾기/명령** 상자 또는 **명령** 창에 별칭을 입력합니다. 예를 들어 **열려 있는 파일** 대화 상자를 표시하는 `>File.OpenFile`을 입력하는 대신 미리 정의된 별칭인 `>of`를 사용할 수 있습니다.

**명령** 창에 `alias`를 입력하여 현재 별칭 및 해당 정의의 목록을 표시합니다. `>cls`를 입력하여 **명령** 창의 내용을 지웁니다. 특정 명령에 대한 별칭을 보려면 `alias <command name>`을 입력하십시오.

인수 포함 여부에 관계없이 Visual Studio 명령 중 하나에 대한 사용자 고유 별칭을 쉽게 만들 수 있습니다. 예를 들어 `File.NewFile MyFile.txt`의 별칭을 만드는 구문은 `alias MyAlias File.NewFile MyFile.txt`입니다. 별칭은 `alias <alias name> /delete`를 사용하여 삭제할 수 있습니다.

다음 표에는 미리 정의된 Visual Studio 명령 별칭 목록이 포함되어 있습니다. 일부 명령에는 두 개 이상의 미리 정의된 별칭이 있습니다. 올바른 구문, 인수 및 해당 명령의 스위치에 대해 설명하는 자세한 항목을 표시하려면 아래의 명령 이름에 대한 링크를 클릭합니다.

|명령 이름|Alias|전체 이름|
|------------------|-----------|-------------------|
|[인쇄 명령](../../ide/reference/print-command.md)|?|Debug.Print|
|[간략한 조사식 명령](../../ide/reference/quick-watch-command.md)|??|Debug.Quickwatch|
|새 프로젝트 추가|AddProj|File.AddNewProject|
|[별칭 명령](../../ide/reference/alias-command.md)|Alias|Tools.Alias|
|자동 창|자동|디버그.자동|
|중단점 창|bl|디버그.중단점|
|중단점 설정/해제|bp|Debug.ToggleBreakPoint|
|호출 스택 창|CallStack|디버그.호출스택|
|책갈피 지우기|ClearBook|편집.책갈피지우기|
|닫습니다|닫습니다|File.Close|
|모든 문서 닫기|CloseAll|Window.CloseAllDocuments|
|모두 지우기|cls|Edit.ClearAll|
|명령 모드|cmd|보기.명령창|
|코드 보기|코드|보기.코드보기|
|[메모리 목록 표시 명령](../../ide/reference/list-memory-command.md)|d|Debug.ListMemory|
|ANSI로 [메모리 목록 표시 명령](../../ide/reference/list-memory-command.md)|da|Debug.ListMemory /Ansi|
|[메모리 명령 목록](../../ide/reference/list-memory-command.md) One Byte 형식|db|Debug.ListMemory /Format:OneByte|
|Four Byte 형식인 ANSI로 [메모리 명령 목록](../../ide/reference/list-memory-command.md)|dc|Debug.ListMemory /Format:FourBytes /Ansi|
|[메모리 명령 목록](../../ide/reference/list-memory-command.md) Four Byte 형식|dd|Debug.ListMemory /Format:FourBytes|
|BOL까지 삭제|DelBOL|Edit.DeleteToBOL|
|EOL까지 삭제|DelEOL|Edit.DeleteToEOL|
|가로 공백 삭제|DelHSp|Edit.DeleteHorizontalWhitespace|
|뷰 디자이너|디자이너|보기.디자이너보기|
|[메모리 명령 목록](../../ide/reference/list-memory-command.md) 부동 형식|df|Debug.ListMemory/Format:Float|
|디스어셈블리 창|disasm|디버그.디스어셈블리|
|[메모리 명령 목록](../../ide/reference/list-memory-command.md) Eight Byte 형식|dq|Debug.ListMemory /Format:EightBytes|
|Unicode로 [메모리 목록 표시 명령](../../ide/reference/list-memory-command.md)|du|Debug.ListMemory /Unicode|
|[문 실행 명령](../../ide/reference/evaluate-statement-command.md)|eval|Debug.EvaluateStatement|
|끝내기|끝내기|File.Exit|
|선택 영역 서식|format|편집.선택영역서식|
|전체 화면|전체 화면|보기.전체화면|
|[시작 명령](../../ide/reference/start-command.md)|g|디버그.시작|
|[이동 명령](../../ide/reference/go-to-command.md)|GotoLn|편집.이동|
|중괄호로 이동|GotoBrace|Edit.GotoBrace|
|F1도움말|도움말|도움말.F1도움말|
|직접 실행 모드|immed|Tools.ImmediateMode|
|텍스트로 파일 삽입|InsertFile|Edit.InsertFileAsText|
|[호출 스택 목록 표시 명령](../../ide/reference/list-call-stack-command.md)|kb|Debug.ListCallStack|
|소문자로 변환|Lcase|편집.소문자로|
|줄 잘라내기|LineCut|편집.줄잘라내기|
|줄 삭제|LineDel|편집.줄삭제|
|멤버 목록|ListMembers|편집.멤버목록|
|지역 창|로컬|디버그.지역|
|[명령 창 출력 로그 명령](../../ide/reference/log-command-window-output-command.md)|로그|Tools.LogCommandWindowOutput|
|명령 창 표시 모드|mark|Tools.CommandWindowMarkMode|
|메모리 창|Memory Memory1|디버그.메모리1|
|메모리 창 2|Memory2|디버그.메모리2|
|메모리 창 3|Memory3|디버그.메모리3|
|메모리 창 4|Memory4|디버그.메모리4|
|[기수 설정 명령](../../ide/reference/set-radix-command.md)|n|Debug.SetRadix|
|[웹 브라우저 표시 명령](../../ide/reference/showwebbrowser-command.md)|nav navigate|View.ShowWebBrowser|
|다음 책갈피|NextBook|편집.다음책갈피|
|[새 파일 명령](../../ide/reference/new-file-command.md)|nf|파일.새파일|
|새 프로젝트|np NewProj|파일.새프로젝트|
|[파일 열기 명령](../../ide/reference/open-file-command.md)|of Open|파일.파일열기|
|[프로젝트 열기 명령](../../ide/reference/open-project-command.md)|op|파일.프로젝트열기|
|정의 부분만 보이기/개요 표시 중지|OutlineDefs StopOutlining|편집.정의부분만보이기|
|프로시저 단위 실행|p|디버그.프로시저단위실행|
|매개 변수 정보|ParamInfo|편집.매개변수정보|
|프로시저 나가기|pr|디버그.프로시저나가기|
|이전 책갈피|PrevBook|편집.이전책갈피|
|파일 인쇄|print|파일.인쇄|
|속성 창|props|보기.속성창|
|중지|q|디버그.디버깅중지|
|다시 실행|다시 실행(redo)|편집.다시실행|
|레지스터 창|레지스터|디버그.레지스터|
|커서까지 실행|rtc|디버그.커서까지실행|
|선택한 항목 저장|저장|파일.선택한항목저장|
|모두 저장|SaveAll|파일.모두저장|
|다른 이름으로 저장|SaveAs|File.SaveSelectedItemsAs|
|[셸 명령](../../ide/reference/shell-command.md)|셸|Tools.Shell|
|파일에서 찾기 중지|StopFind|Edit.FindInFiles /stop|
|앵커 바꾸기|SwapAnchor|편집.앵커바꾸기|
|한 단계씩 코드 실행|t|디버그.한단계씩코드실행|
|선택 영역을 탭으로 바꿈|탭으로 바꿈|Edit.TabifySelection|
|작업 목록 창|TaskList|보기.작업목록|
|스레드 창|스레드|Debug.Threads|
|가로 바둑판식 배열|TileH|Window.TileHorizontally|
|세로 바둑판식 배열|TileV|Window.TileVertically|
|책갈피 설정/해제|ToggleBook|편집.책갈피설정해제|
|도구 상자 창|도구 상자|보기.도구상자|
|[디스어셈블리 목록 표시 명령](../../ide/reference/list-disassembly-command.md)|u|Debug.ListDisassembly|
|대문자로|Ucase|편집.대문자로|
|실행 취소|실행 취소|편집.실행취소|
|선택 영역을 탭으로 바꾸지 않음|Untabify|Edit.UntabifySelection|
|조사식 창|조사식|Debug.WatchN|
|자동 줄 바꿈 설정/해제|WordWrap|편집.자동줄바꿈설정해제|
|프로세스 목록 표시|&#124;|Debug.ListProcesses|
|[스레드 목록 표시 명령](../../ide/reference/list-threads-command.md)|~ ~*k ~\*kb|Debug.ListThreads Debug.ListTheads /AllThreads|

## <a name="see-also"></a>참고 항목

- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [명령 창](../../ide/reference/command-window.md)
- [찾기/명령 상자](../../ide/find-command-box.md)

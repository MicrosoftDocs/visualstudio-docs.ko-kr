---
title: 명령 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Visual Studio, commands
- commands, Visual Studio
- command syntax
ms.assetid: 76ffa394-ee89-4629-aba9-1a62b72e6cc1
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b6ad913e418f2f13bd196925b3c085b9d5c7efca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667455"
---
# <a name="visual-studio-commands"></a>Visual Studio 명령
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio에서는 **명령** 창, **직접 실행** 창 또는 **찾기/명령** 상자에서 명령을 호출할 수 있습니다. 각각의 경우 검색 또는 디버그 작업이 아닌 명령을 따라야 함을 나타내기 위해 보다 큼 부호(`>`)가 사용됩니다.

 **키보드, 환경 옵션** 대화 상자에서 명령 및 구문의 전체 목록을 찾을 수 있습니다.

 Visual Studio 명령의 이스케이프 문자는 캐럿(^) 문자입니다. 이는 바로 다음 문자가 제어 문자가 아닌 문자 그대로 해석된다는 것을 의미합니다. 이스케이프 문자는 매개 변수 또는 스위치 값에 곧은 큰따옴표("), 공백, 선행 슬래시, 캐럿 등 또는 리터럴 문자를 포함하기 위해 사용할 수 있습니다(스위치 이름 제외). 예를 들면 다음과 같습니다.

```
>Edit.Find ^^t /regex
```

 캐럿은 따옴표 내부에 있든 외부에 있든 기능이 동일합니다. 캐럿이 줄에서 마지막 문자인 경우 무시됩니다.

 IDE의 지역화된 버전에서는 IDE의 기본 언어 또는 영어로 명령 이름을 입력할 수 있습니다. 예를 들어 프랑스어 IDE에서 동일한 명령을 실행하려면 `File.NewFile` 또는 `Fichier.NouveauFichier` 를 입력할 수 있습니다.

 많은 명령에 별칭이 있습니다. 명령 별칭 목록은 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)를 참조하세요.

 다음 명령은 인수 및/또는 스위치를 사용합니다.

|명령 이름|설명|
|------------------|-----------------|
|[기존 항목 추가](../../ide/reference/add-existing-item-command.md)|현재 솔루션에 기존 파일을 추가하고 엽니다.|
|[기존 프로젝트 추가](../../ide/reference/add-existing-project-command.md)|현재 솔루션에 기존 프로젝트를 추가합니다.|
|[새 항목 추가](../../ide/reference/add-new-item-command.md)|현재 솔루션에 .htm, .css, .txt 또는 프레임셋 같은 새 솔루션 항목을 추가하고 엽니다.|
|[별칭](../../ide/reference/alias-command.md)|전체 명령에 대한 새 별칭, 전체 명령 및 인수에 대한 새 별칭 또는 심지어 또 다른 별칭을 만듭니다.|
|[문 실행](../../ide/reference/evaluate-statement-command.md)|지정된 문을 평가 및 표시합니다.|
|[찾기](../../ide/reference/find-command.md)|**찾기 및 바꾸기** 컨트롤에서 사용할 수 있는 옵션의 하위 집합을 사용하여 파일을 검색합니다.|
|[파일에서 찾기](../../ide/reference/find-in-files-command.md)|[파일에서 찾기](../../ide/find-in-files.md)에서 사용할 수 있는 옵션의 하위 집합을 사용하여 파일을 검색합니다.|
|[로 가다](../../ide/reference/go-to-command.md)|지정된 줄로 커서를 이동합니다.|
|[호출 스택 목록 표시](../../ide/reference/list-call-stack-command.md)|현재 호출 스택을 표시합니다.|
|[디스어셈블리 목록 표시](../../ide/reference/list-disassembly-command.md)|디버그 프로세스를 시작하고 오류 처리 방식을 지정할 수 있습니다.|
|[메모리 목록 표시](../../ide/reference/list-memory-command.md)|지정된 메모리 범위의 내용을 표시합니다.|
|[모듈 나열](../../ide/reference/list-modules-command.md)|현재 프로세스에 대한 모듈을 나열합니다.|
|[레지스터 목록 표시](../../ide/reference/list-registers-command.md)|레지스터의 목록을 표시합니다.|
|[소스 목록 표시](../../ide/reference/list-source-command.md)|소스 코드의 지정된 줄을 표시합니다.|
|[스레드 목록 표시](../../ide/reference/list-threads-command.md)|현재 프로그램의 스레드 목록을 표시합니다.|
|[명령 창 출력 로그](../../ide/reference/log-command-window-output-command.md)|명령 창의 모든 입력 및 출력을 파일로 복사합니다.|
|[새 파일](../../ide/reference/new-file-command.md)|새 파일을 만들고 현재 선택한 프로젝트에 추가합니다.|
|[파일 열기](../../ide/reference/open-file-command.md)|기존 파일을 열고 편집기를 지정할 수 있습니다.|
|[프로젝트 열기](../../ide/reference/open-project-command.md)|기존 프로젝트를 열고 현재 솔루션에 프로젝트를 추가할 수 있습니다.|
|[솔루션 열기](../../ide/reference/open-solution-command.md)|기존 솔루션을 엽니다.|
|[인쇄](../../ide/reference/print-command.md)|식을 계산하고 결과 또는 지정된 텍스트를 표시합니다.|
|[간략 한 조사식 명령](../../ide/reference/quick-watch-command.md)|**간략한 조사식** 대화 상자의 **식** 필드에 선택한 텍스트 또는 지정한 텍스트를 표시합니다.|
|[바꾸기](../../ide/reference/replace-command.md)|**찾기 및 바꾸기** 컨트롤에서 사용할 수 있는 옵션의 하위 집합을 사용하여 파일의 텍스트를 바꿉니다.|
|[파일에서 바꾸기](../../ide/reference/replace-in-files-command.md)|[파일에서 바꾸기](../../ide/replace-in-files.md)에서 사용할 수 있는 옵션의 하위 집합을 사용하여 파일의 텍스트를 바꿉니다.|
|[현재 스택 프레임 설정](../../ide/reference/set-current-stack-frame-command.md)|특정 스택 프레임을 볼 수 있습니다.|
|[현재 스레드 설정](../../ide/reference/set-current-thread-command.md)|특정 스레드를 볼 수 있습니다.|
|[기수 설정](../../ide/reference/set-radix-command.md)|보려는 바이트 수를 결정합니다.|
|[셸](../../ide/reference/shell-command.md)|명령 프롬프트에서 명령이 실행된 것처럼 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 내에서 프로그램을 시작합니다.|
|[ShowWebBrowser 명령](../../ide/reference/showwebbrowser-command.md)|IDE(통합 개발 환경) 내부 또는 외부의 웹 브라우저 창에서 지정하는 URL을 표시합니다.|
|[시작](../../ide/reference/start-command.md)|디버그 프로세스를 시작하고 오류 처리 방식을 지정할 수 있습니다.|
|[Path](../../ide/reference/symbol-path-command.md)|디버거에서 기호를 검색할 디렉터리 목록을 설정합니다.|
|[중단점 설정/해제](../../ide/reference/toggle-breakpoint-command.md)|파일의 현재 위치에서 현재 상태에 따라 중단점을 켜거나 끕니다.|
|[조사식 명령](../../ide/reference/watch-command.md)|**조사식** 창의 지정된 인스턴스를 만들고 엽니다.|

## <a name="see-also"></a>관련 항목
 [명령 창](../../ide/reference/command-window.md) [찾기/명령 상자](../../ide/find-command-box.md) [Visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)

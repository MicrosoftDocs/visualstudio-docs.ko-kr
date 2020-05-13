---
title: 명령
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio, commands
- commands, Visual Studio
- command syntax
ms.assetid: 76ffa394-ee89-4629-aba9-1a62b72e6cc1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac0284ce274791f21c9c0f85d265d92a7097cb09
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596374"
---
# <a name="visual-studio-commands"></a>Visual Studio 명령

**명령** 창, **직접 실행** 창 또는 **찾기/명령** 상자에서 Visual Studio 명령을 입력할 수 있습니다. 각 경우에서 보다 큼 기호(`>`)는 검색 또는 디버그 작업이 아닌 명령이 뒤에 표시됨을 나타냅니다.

**도구** > **옵션** > **환경**의 **키보드** 페이지에서 전체 명령 목록 및 해당 구문을 확인할 수 있습니다.

IDE의 지역화된 버전에서는 IDE의 기본 언어 또는 영어로 명령 이름을 입력할 수 있습니다. 예를 들어 프랑스어 IDE에서 동일한 명령을 실행하려면 `File.NewFile` 또는 `Fichier.NouveauFichier` 를 입력할 수 있습니다.

많은 명령에 별칭이 있습니다. 명령 별칭 목록은 [명령 별칭](../../ide/reference/visual-studio-command-aliases.md)을 참조하세요. 명령 바로 가기 키는 [Visual Studio의 기본 바로 가기 키](../default-keyboard-shortcuts-in-visual-studio.md)를 참조하세요.

## <a name="escape-character"></a>이스케이프 문자

Visual Studio 명령의 이스케이프 문자는 캐럿(^)입니다. 이스케이프 문자는 바로 뒤의 문자가 제어 문자가 아닌 문자 그대로 해석됨을 의미합니다. 이스케이프 문자는 매개 변수 또는 스위치 값에 곧은 큰따옴표("), 공백, 선행 슬래시, 캐럿 등 또는 리터럴 문자를 포함하기 위해 사용할 수 있습니다(스위치 이름 제외). 예를 들어:

```
>Edit.Find ^^t /regex
```

캐럿은 따옴표 내부에 있든 외부에 있든 기능이 동일합니다. 캐럿이 줄에서 마지막 문자인 경우에는 무시됩니다.

## <a name="commands-with-arguments"></a>인수가 있는 명령

다음 명령은 인수 또는 스위치를 사용합니다.

| 명령 이름 | 설명 |
| - | - |
| [기존 항목 추가](../../ide/reference/add-existing-item-command.md) | 현재 솔루션에 기존 파일을 추가하고 엽니다. |
| [기존 프로젝트 추가](../../ide/reference/add-existing-project-command.md) | 현재 솔루션에 기존 프로젝트를 추가합니다. |
| [새 항목 추가](../../ide/reference/add-new-item-command.md) | 현재 솔루션에 .htm, .css, .txt 또는 프레임셋 같은 새 솔루션 항목을 추가하고 엽니다. |
| [Alias](../../ide/reference/alias-command.md) | 전체 명령에 대한 새 별칭, 전체 명령 및 인수에 대한 새 별칭 또는 심지어 또 다른 별칭을 만듭니다. |
| [문 실행](../../ide/reference/evaluate-statement-command.md) | 지정된 문을 평가 및 표시합니다. |
| [Find](../../ide/reference/find-command.md) | **찾기 및 바꾸기** 컨트롤에서 사용할 수 있는 옵션의 하위 집합을 사용하여 파일을 검색합니다. |
| [파일에서 찾기](../../ide/reference/find-in-files-command.md) | [파일에서 찾기](../../ide/find-in-files.md)에서 사용할 수 있는 옵션의 하위 집합을 사용하여 파일을 검색합니다. |
| [이동](../../ide/reference/go-to-command.md) | 지정된 줄로 커서를 이동합니다. |
| [호출 스택 목록 표시](../../ide/reference/list-call-stack-command.md) | 현재 호출 스택을 표시합니다. |
| [디스어셈블리 목록 표시](../../ide/reference/list-disassembly-command.md) | 디버그 프로세스를 시작하고 오류 처리 방식을 지정할 수 있습니다. |
| [메모리 목록 표시](../../ide/reference/list-memory-command.md) | 지정된 메모리 범위의 내용을 표시합니다. |
| [모듈 목록 표시](../../ide/reference/list-modules-command.md) | 현재 프로세스에 대한 모듈을 나열합니다. |
| [레지스터 목록 표시](../../ide/reference/list-registers-command.md) | 레지스터의 목록을 표시합니다. |
| [소스 목록 표시](../../ide/reference/list-source-command.md) | 소스 코드의 지정된 줄을 표시합니다. |
| [스레드 목록 표시](../../ide/reference/list-threads-command.md) | 현재 프로그램의 스레드 목록을 표시합니다. |
| [명령 창 출력 로그](../../ide/reference/log-command-window-output-command.md) | 명령 창의 모든 입력 및 출력을 파일로 복사합니다. |
| [새 파일](../../ide/reference/new-file-command.md) | 새 파일을 만들고 현재 선택한 프로젝트에 추가합니다. |
| [파일 열기](../../ide/reference/open-file-command.md) | 기존 파일을 열고 편집기를 지정할 수 있습니다. |
| [프로젝트 열기](../../ide/reference/open-project-command.md) | 기존 프로젝트를 열고 현재 솔루션에 프로젝트를 추가할 수 있습니다. |
| [인쇄](../../ide/reference/print-command.md) | 식을 계산하고 결과 또는 지정된 텍스트를 표시합니다. |
| [간략한 조사식 명령](../../ide/reference/quick-watch-command.md) | **간략한 조사식** 대화 상자의 **식** 필드에 선택한 텍스트 또는 지정한 텍스트를 표시합니다. |
| [바꾸기](../../ide/reference/replace-command.md) | **찾기 및 바꾸기** 컨트롤에서 사용할 수 있는 옵션의 하위 집합을 사용하여 파일의 텍스트를 바꿉니다. |
| [파일에서 바꾸기](../../ide/reference/replace-in-files-command.md) | [파일에서 바꾸기](../../ide/replace-in-files.md)에서 사용할 수 있는 옵션의 하위 집합을 사용하여 파일의 텍스트를 바꿉니다. |
| [현재 스택 프레임 설정](../../ide/reference/set-current-stack-frame-command.md) | 특정 스택 프레임을 볼 수 있습니다. |
| [현재 스레드 설정](../../ide/reference/set-current-thread-command.md) | 특정 스레드를 볼 수 있습니다. |
| [기수 설정](../../ide/reference/set-radix-command.md) | 보려는 바이트 수를 결정합니다. |
| [셸](../../ide/reference/shell-command.md) | 명령 프롬프트에서 명령이 실행된 것처럼 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 내에서 프로그램을 시작합니다. |
| [웹 브라우저 표시 명령](../../ide/reference/showwebbrowser-command.md) | IDE(통합 개발 환경) 내부 또는 외부의 웹 브라우저 창에서 지정하는 URL을 표시합니다. |
| [Start](../../ide/reference/start-command.md) | 디버그 프로세스를 시작하고 오류 처리 방식을 지정할 수 있습니다. |
| [Path](../../ide/reference/symbol-path-command.md) | 디버거에서 기호를 검색할 디렉터리 목록을 설정합니다. |
| [중단점 설정/해제](../../ide/reference/toggle-breakpoint-command.md) | 파일의 현재 위치에서 현재 상태에 따라 중단점을 켜거나 끕니다. |
| [조사식 명령](../../ide/reference/watch-command.md) | **조사식** 창의 지정된 인스턴스를 만들고 엽니다. |

## <a name="see-also"></a>참조

- [명령 창](../../ide/reference/command-window.md)
- [찾기/명령 상자](../../ide/find-command-box.md)
- [Visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)

---
title: 호출 스택 목록 표시 명령
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f62852550c161566832a7ab78d4058d1d14028f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72748715"
---
# <a name="list-call-stack-command"></a>호출 스택 목록 표시 명령
현재 호출 스택을 표시합니다.

## <a name="syntax"></a>구문

```cmd
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]
[/ShowExternalCode:yes|no] [Thread:n] [index]
```

## <a name="arguments"></a>인수

`index`\
(선택 사항) 현재 스택 프레임을 설정하고 출력을 표시하지 않습니다.

## <a name="switches"></a>스위치
각 스위치는 전체 양식 및 약식을 사용하여 호출될 수 있습니다.

/Count:`number` [또는] /C:`number`

(선택 사항) 표시할 최대 호출 스택 수입니다. 기본값은 제한되지 않습니다.

/ShowTypes:`yes`&#124;`no` [또는] /T:`yes`&#124;`no`

(선택 사항) 매개 변수 형식을 표시할지 여부를 지정합니다. 기본값은 `yes`입니다.

/ShowNames:`yes`&#124;`no` [또는] /N:`yes`&#124;`no`

(선택 사항) 매개 변수 이름을 표시할지 여부를 지정합니다. 기본값은 `yes`입니다.

/ShowValues:`yes`&#124;`no` [또는] /V:`yes`&#124;`no`

(선택 사항) 매개 변수 값을 표시할지 여부를 지정합니다. 기본값은 `yes`입니다.

/ShowModule:`yes`&#124;`no` [또는] /M:`yes`&#124;`no`

(선택 사항) 모듈 이름을 표시할지 여부를 지정합니다. 기본값은 `yes`입니다.

/ShowLineOffset:`yes`&#124;`no` [또는] /#:`yes`&#124;`no`

(선택 사항) 줄 오프셋을 표시할지 여부를 지정합니다. 기본값은 `no`입니다.

/ShowByteOffset:`yes`&#124;`no` [또는] /B:`yes`&#124;`no`

(선택 사항) 바이트 오프셋을 표시할지 여부를 지정합니다. 기본값은 `no`입니다.

/ShowLanguage:`yes`&#124;`no` [또는] /L:`yes`&#124;`no`

(선택 사항) 언어를 표시할지 여부를 지정합니다. 기본값은 `no`입니다.

/IncludeCallsAcrossThreads:`yes`&#124;`no` [또는] /I:`yes`&#124;`no`

(선택 사항) 호출을 포함할지 아니면 또는 다른 스레드에서 가져올지를 지정합니다. 기본값은 `no`입니다.

/ShowExternalCode:`yes`&#124;`no`

(선택 사항) 호출 스택에 대해 내 코드만 표시할지를 지정합니다. 내 코드만을 해제하는 경우 모든 비사용자 코드가 표시됩니다. 내 코드만을 사용하는 경우 비사용자 코드는 호출 스택 출력에서 `[external]`로 표시됩니다.

스레드:`n`

(선택 사항) 스레드 `n`에 대한 호출 스택을 표시합니다. 스레드가 지정되지 않은 경우 현재 스레드에 대한 호출 스택을 표시합니다.

## <a name="remarks"></a>설명
인수 또는 스위치에 대한 변경 내용은 이 명령의 이후 호출에 적용됩니다. Debug.ListCallStackby 자체를 실행하면 전체 호출 스택이 표시됩니다. 예를 들어 인덱스를 지정하는 경우

```cmd
Debug.ListCallStack 2
```

현재 스택 프레임이 해당 프레임으로 설정됩니다(이 경우 두 번째 프레임).

미리 정의된 별칭(kb)을 사용하여 이 명령을 작성할 수도 있습니다. 예를 들어 다음과 같이 입력하여

```cmd
kb 2
```

현재 스택 프레임을 두 번째 프레임으로 설정할 수 있습니다.

## <a name="example"></a>예제

```cmd
>Debug.CallStack /Count:4 /ShowTypes:yes
```

## <a name="see-also"></a>참고 항목

- [디스어셈블리 목록 표시 명령](../../ide/reference/list-disassembly-command.md)
- [스레드 목록 표시 명령](../../ide/reference/list-threads-command.md)
- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [명령 창](../../ide/reference/command-window.md)
- [찾기/명령 상자](../../ide/find-command-box.md)
- [Visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)
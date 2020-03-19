---
title: 중단점 설정/해제 명령
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d393890e6166b4a4ef53c9520a556e9a9edd64d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75597323"
---
# <a name="toggle-breakpoint-command"></a>중단점 설정/해제 명령
파일의 현재 위치에서 현재 상태에 따라 중단점을 켜거나 끕니다.

## <a name="syntax"></a>구문

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>인수

`text`\
(선택 사항) 텍스트를 지정하는 경우 해당 줄은 명명된 중단점으로 표시됩니다. 그렇지 않은 경우 해당 줄은 F9 키를 누를 때처럼 명명되지 않은 중단점으로 표시됩니다.

## <a name="example"></a>예제
다음 예제에서는 현재 중단점을 설정/해제합니다.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>참고 항목

- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [명령 창](../../ide/reference/command-window.md)
- [찾기/명령 상자](../../ide/find-command-box.md)
- [Visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)

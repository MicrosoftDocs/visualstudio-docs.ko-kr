---
title: 중단점 설정/해제 명령
description: 중단점 설정/해제 명령을 사용하여 파일의 현재 위치에서 현재 상태에 따라 중단점을 설정하거나 해제하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b65144271f91d518dd6649fa1e97fc627d1b0009
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560969"
---
# <a name="toggle-breakpoint-command"></a>중단점 설정/해제 명령
파일의 현재 위치에서 현재 상태에 따라 중단점을 켜거나 끕니다.

## <a name="syntax"></a>구문

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>인수

`text`\
선택 사항입니다. 텍스트를 지정하는 경우 해당 줄은 명명된 중단점으로 표시됩니다. 그렇지 않은 경우 해당 줄은 F9 키를 누를 때처럼 명명되지 않은 중단점으로 표시됩니다.

## <a name="example"></a>예
다음 예제에서는 현재 중단점을 설정/해제합니다.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>참고 항목

- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [명령 창](../../ide/reference/command-window.md)
- [찾기/명령 상자](../../ide/find-command-box.md)
- [Visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)

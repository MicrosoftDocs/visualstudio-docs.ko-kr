---
title: 현재 스택 프레임 설정 명령
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f70f5ebfc80933f38f1543d5eb42f01fb470298f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85769718"
---
# <a name="set-current-stack-frame-command"></a>현재 스택 프레임 설정 명령
특정 스택 프레임을 설정할 수 있습니다.

## <a name="syntax"></a>구문

```cmd
Debug.SetCurrentStackFrame index
```

## <a name="arguments"></a>인수
`index`

필수 사항입니다. 해당 인덱스로 스택 프레임을 선택합니다.

## <a name="example"></a>예제

```cmd
>Debug.SetCurrentStackFrame 1
```

## <a name="see-also"></a>참고 항목

- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [명령 창](../../ide/reference/command-window.md)
- [찾기/명령 상자](../../ide/find-command-box.md)
- [Visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)
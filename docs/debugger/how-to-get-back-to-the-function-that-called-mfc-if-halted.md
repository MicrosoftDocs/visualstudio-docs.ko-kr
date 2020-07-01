---
title: 중지되면 MFC를 호출한 함수로 돌아가기 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.mfc
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef96bab28b1a17d4f20728a393511720fd10c624
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349473"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>방법: 중지된 경우 MFC를 호출한 함수로 돌아가기

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [재설정 설정](../ide/environment-settings.md#reset-settings)을 참조하세요.

**디버그** 메뉴의 **중단** 명령을 사용하여 프로그램을 중단했을 때 MFC에서 중지되었고 코드에 문제가 있다고 판단되면 호출 스택 창을 사용하여 함수로 되돌아갈 수 있습니다. 자세한 내용은 [방법: 호출 스택 창 사용](../debugger/how-to-use-the-call-stack-window.md)을 참조하세요.

때로는 코드가 메시지 펌프에서 손상될 수도 있습니다. 그럴 경우 호출 스택에는 사용자 코드가 들어 있지 않습니다. 이 문제가 발생하지 않도록 하려면 **중단** 명령 대신 중단점을 사용합니다. 이 경우 조건 및 적중 횟수도 함께 사용할 수 있습니다. 자세한 내용은 [Breakpoints and Tracepoints](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583)을 참조하세요.

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>MFC를 호출한 함수로 이동

- **호출 스택** 창을 사용합니다.

## <a name="see-also"></a>참조

- [네이티브 코드 디버그 FAQ](../debugger/debugging-native-code-faqs.md)
- [네이티브 코드 디버그](../debugger/debugging-native-code.md)
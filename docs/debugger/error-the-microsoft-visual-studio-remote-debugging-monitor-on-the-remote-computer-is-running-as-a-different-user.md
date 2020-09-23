---
title: 원격 컴퓨터의 Microsoft Visual Studio 원격 디버깅 모니터가 다른 사용자로 실행 중입니다.
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5acf69b980221c0d953e22e66502672477656dbc
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851764"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>오류: 원격 컴퓨터의 Microsoft Visual Studio 원격 디버깅 모니터가 다른 사용자로 실행 중입니다.
원격으로 디버깅할 때 다음 오류 메시지가 나타날 수 있습니다.

 원격 컴퓨터의 Microsoft Visual Studio 원격 디버깅 모니터가 다른 사용자로 실행 중입니다.

## <a name="cause"></a>원인
 이 메시지는 인증 안 함 모드에서 디버깅할 때 msvsmon을 시작한 사용자와 Visual Studio를 실행하는 사용자가 서로 다른 경우에 나타납니다.

## <a name="solution"></a>솔루션
 가장 안전한 최상의 해결책은 Visual Studio와 동일한 사용자 계정에서 원격 디버깅 모니터(msvsmon.exe)를 실행하는 것입니다. 이렇게 할 수 없는 경우 원격 디버깅 모니터 **옵션** 대화 상자에서 **모든 사용자가 디버깅할 수 있도록 허용** 옵션을 선택하여 다른 계정에서 원격 디버깅 모니터를 실행할 수 있습니다.

> [!CAUTION]
> 다른 사용자에게 연결 권한을 부여하면 잘못된 원격 디버깅 세션에 실수로 연결할 가능성이 있습니다. **인증 안 함** 모드에서 디버깅하는 것은 안전하지 않으므로 이 모드를 사용할 때는 특히 주의해야 합니다.

## <a name="see-also"></a>참조
- [원격 디버깅 오류 및 문제 해결](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)
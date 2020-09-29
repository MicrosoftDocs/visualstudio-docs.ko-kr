---
title: 예외 검사
titleSuffix: ''
ms.date: 1/18/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- exception helper, debugger, exception
- debugging [Visual Studio], exception helper, Examine an exception
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d0084abff760ff227b20137cd55d905b57e1a18
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852500"
---
# <a name="inspect-an-exception-using-the-exception-helper"></a>예외 도우미를 사용하여 예외 검사 

예외를 처리하는 것은 기술 또는 전문 지식 수준에 관계없이 공통적인 문제입니다. 코드에서 예외 때문에 문제가 발생하는 이유를 파악하는 것은 어려울 수 있습니다. Visual Studio에서 예외를 디버그하는 경우 문제를 더 빨리 디버그하는 데 도움이 되는 관련 예외 정보를 제공하여 이 어려움을 완화하려고 합니다.

![예외 도우미](media/debugger-exception-helper-default.png)

## <a name="pause-on-the-exception"></a>예외 발생 시 일시 중지
디버거가 예외에서 중단되면 해당 코드 줄의 오른쪽에 예외 오류 아이콘이 표시됩니다. 비모달 예외 도우미가 예외 아이콘 근처에 표시됩니다.

![코드 줄 옆의 예외 도우미](media/debugger-exception-helper-locerror.png)

## <a name="inspect-exception-info"></a>예외 정보 검사
예외 도우미에서 예외 형식 및 예외 메시지를 즉시 읽고 예외가 throw되었는지 또는 처리되지 않았는지 확인할 수 있습니다. **세부 정보 보기** 링크를 클릭하여 예외 개체의 속성을 검사하고 볼 수 있습니다.

## <a name="analyze-null-references"></a>Null 참조 분석
Visual Studio 2017부터 .Net 및 C/C++ 코드 모두에 대해 `NullReferenceException` 또는 `AccessViolation`이 적중되면 예외 도우미에 Null 분석 정보가 표시됩니다. 분석은 예외 메시지 아래에 텍스트로 표시됩니다. 아래 그림에서 정보는 "**s** was null."로 표시됩니다.

![예외 도우미 Null 분석](media/debugger-exception-helper-default.png)


> [!NOTE]
> 관리 코드의 Null 참조 분석에는 .NET 버전 4.6.2가 필요합니다. UWP(유니버설 Windows 플랫폼) 및 기타 모든 .NET Core 애플리케이션에서 Null 분석이 현재 지원되지 않습니다. JIT(Just-In-Time) 코드 최적화가 없는 코드를 디버그하는 동안에만 사용할 수 있습니다.

## <a name="configure-exception-settings"></a>예외 설정 구성 
예외 도우미의 **예외 설정** 섹션에서 현재 형식의 예외가 throw될 때 중단하도록 디버거를 구성할 수 있습니다. 디버거가 throw된 예외에서 일시 중지되면 확인란을 사용하여 나중에 해당 예외가 throw될 때 중단을 사용하지 않도록 설정할 수 있습니다. 이 특정 모듈에서 throw될 때 이 특정 예외에서 중단하지 않으려면 **예외 설정** 창에서 다음에서 **throw되는 경우를 제외:** 아래에서 모듈 이름 옆의 확인란을 선택합니다. 

## <a name="inspect-inner-exceptions"></a>내부 예외 검사 
예외에 내부 예외([InnerException](/dotnet/api/system.exception.innerexception))가 있는 경우 예외 도우미에서 볼 수 있습니다. 여러 예외가 있는 경우 호출 스택 위에 표시되는 왼쪽 및 오른쪽 화살표를 사용하여 탐색할 수 있습니다.

![내부 예외가 있는 예외 도우미](media/debugger-exception-helper-innerexception.png)

## <a name="inspect-rethrown-exceptions"></a>다시 throw되는 예외 검사
예외가 `thrown`된 경우 예외 도우미는 처음으로 예외가 throw되었을 때의 호출 스택을 보여 줍니다. 예외가 여러 번 throw된 경우에는 원래 예외의 호출 스택만 표시됩니다.

![다시 throw된 예외가 있는 예외 도우미](media/debugger-exception-helper-innerexception.png)

## <a name="share-a-debug-session-with-live-share"></a>Live Share를 사용하여 디버그 세션 공유
예외 도우미에서 **Live Share 세션 시작...** 링크를 사용하여 [Live Share](/visualstudio/liveshare/) 세션을 시작할 수 있습니다. Live Share 세션에 참가하는 모든 사용자는 다른 디버그 정보와 함께 예외 도우미를 볼 수 있습니다.
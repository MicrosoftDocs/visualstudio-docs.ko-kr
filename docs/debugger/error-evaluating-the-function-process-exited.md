---
title: '오류: 대상 프로세스가 &#39;function&#39; 함수를 확인하는 중 &#39;code&#39; 코드로 종료되었습니다. | Microsoft Docs'
ms.date: 4/06/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.process_exit_during_func_eval
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75d82b6011a0dfa7f2c388e7d5f39a9ebabcd663
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850814"
---
# <a name="error-the-target-process-exited-with-code-39code39-while-evaluating-the-function-39function39"></a>오류: 대상 프로세스가 &#39;function&#39; 함수를 확인하는 중 &#39;code&#39; 코드로 종료되었습니다.

전체 메시지 텍스트: 대상 프로세스가 'function' 함수를 확인하는 중 'code' 코드로 종료되었습니다.

.NET 개체의 상태를 더 쉽게 검사할 수 있도록 디버거는 디버그된 프로세스가 자동으로 추가 코드(일반적으로 속성 getter 메서드 및 `ToString` 함수)를 실행하도록 강제 적용합니다. 대부분의 시나리오에서는 이러한 함수가 성공적으로 완료되거나 디버거가 catch할 수 있는 예외를 throw합니다. 하지만 예외가 커널 경계를 넘거나 사용자 메시지 펌프가 필요하거나 복구할 수 없기 때문에 예외를 catch할 수 없는 경우도 있습니다. 따라서 프로세스를 명시적으로 종료하거나(예: `ExitProcess()` 호출) catch할 수 없는 처리되지 않은 예외를 throw하는(예: `StackOverflowException`) 코드를 실행하는 속성 getter 또는 ToString 메서드는 디버그된 프로세스를 종료하고 디버그 세션을 종료합니다. 이 오류 메시지가 표시되면 오류가 발생한 것입니다.

이 문제가 발생하는 일반적인 이유 중 하나는 디버거가 자신을 호출하는 속성을 확인할 때 스택 오버플로 예외가 발생할 수 있다는 점입니다. 스택 오버플로 예외는 복구할 수 없으므로 대상 프로세스가 종료됩니다.

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

이 문제에 대한 가능한 해결 방법은 다음 2가지가 있습니다.

### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>해결 방법 #1: 디버거가 getter 속성 또는 ToString 메서드를 호출하지 않도록 방지 

오류 메시지는 디버거가 호출하려고 시도한 함수의 이름을 알려줍니다. 함수 이름을 사용하여 **직접 실행** 창에서 해당 함수를 다시 확인하면 확인을 디버그할 수 있습니다. **자동/지역/조사식** 창에서 하는 암시적 확인과 달리, **직접 실행** 창에서 확인하는 경우 처리되지 않은 예외가 발생하면 디버거가 중단되므로 확인을 디버그할 수 있습니다.

함수를 수정할 수 있는 경우 디버거가 속성 getter 또는 `ToString` 메서드를 호출하지 않도록 방지할 수 있습니다. 다음 작업 중 하나를 수행하세요.

* 속성 getter 또는 ToString 메서드 이외의 다른 코드 형식으로 메서드를 변경하면 문제가 해결됩니다.
    또는
* (`ToString`의 경우) 형식에 `DebuggerDisplay` 특성을 정의하고 디버거가 `ToString` 이외의 항목을 확인하도록 할 수 있습니다.
    또는
* (속성 getter의 경우) 속성에 `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` 특성을 지정합니다. API 호환성을 위해 속성을 유지해야 하는 메서드가 있으면 유용할 수 있으나 정말로 메서드여야 합니다.

메서드를 수정할 수 없는 경우 대체 명령으로 대상 프로세스가 중단되도록 하고 확인을 다시 시도할 수 있습니다.

### <a name="solution-2-disable-all-implicit-evaluation"></a>해결 방법 #2: 모든 암시적 확인 사용 안 함

이전 해결 방법으로 문제가 해결되지 않는 경우 **도구** > **옵션**으로 이동하여 **디버깅** > **일반** > **속성 확인 및 기타 암시적 함수 호출 사용** 설정을 선택 취소합니다. 이렇게 하면 대부분의 암시적 함수 확인이 사용하지 않도록 설정되며 문제가 해결됩니다.

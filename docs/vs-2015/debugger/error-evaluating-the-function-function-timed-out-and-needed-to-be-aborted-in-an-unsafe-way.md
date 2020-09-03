---
title: '오류: &#39;function&#39; 함수를 확인하는 중 시간이 초과하여 안전하지 않은 방식으로 중단해야 했습니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.topic: reference
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
ms.assetid: 0a9f70ed-21ad-4a10-8535-b9c5885ad8f4
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a27bf67770eef770fddef0301a804e6c45579539
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387124"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>오류: &#39;function&#39; 함수를 확인하는 중 시간이 초과하여 안전하지 않은 방식으로 중단해야 했습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

전체 메시지 텍스트: ‘function’ 함수를 확인하는 중 시간이 초과하여 안전하지 않은 방식으로 중단해야 했습니다. 이로 인해 대상 프로세스가 손상되었을 수 있습니다. 

.NET 개체의 상태를 더 쉽게 검사할 수 있도록 디버거는 디버그된 프로세스가 자동으로 추가 코드(일반적으로 속성 getter 메서드 및 ToString 함수)를 실행하도록 강제 적용합니다. 대부분의 시나리오에서는 이러한 함수가 신속하게 완료되며 디버깅을 훨씬 쉽게 수행할 수 있습니다. 그러나 디버거는 샌드박스에서 응용 프로그램을 실행 하지 않습니다. 따라서 응답을 중지하는 네이티브 함수로 호출되는 속성 getter 또는 ToString 메서드에 복구가 불가능한 오랜 시간 초과가 발생할 수 있습니다. 이 오류 메시지가 표시되면 오류가 발생한 것입니다.
 
이 문제가 발생하는 일반적인 이유 중 하나는 디버거가 속성을 확인할 때 검사 중인 스레드만 실행되도록 허용하는 점입니다. 따라서 속성이 디버깅 된 응용 프로그램 내에서 실행 될 때까지 대기 하 고 .NET 런타임에서 중단할 수 없는 방식으로 대기 중인 경우에는이 문제가 발생 합니다.
 
## <a name="to-correct-this-error"></a>이 오류를 해결하려면
 
이 문제에 대 한 세 가지 해결 방법이 있습니다.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>해결 방법 #1: 디버거가 getter 속성 또는 ToString 메서드를 호출하지 않도록 방지
 
오류 메시지는 디버거가 호출하려고 시도한 함수의 이름을 알려줍니다. 함수를 수정할 수 있는 경우 디버거가 속성 getter 또는 ToString 메서드를 호출하지 않도록 방지할 수 있습니다. 다음 작업 중 하나를 수행하세요.
 
* 속성 getter 또는 ToString 메서드 이외의 다른 코드 형식으로 메서드를 변경하면 문제가 해결됩니다.
    또는
* (ToString의 경우) 형식에 DebuggerDisplay 특성을 정의하고 디버거가 ToString 이외의 항목을 확인하도록 할 수 있습니다.
    또는
* (속성 getter의 경우) 속성에 `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` 특성을 지정합니다. API 호환성을 위해 속성을 유지해야 하는 메서드가 있으면 유용할 수 있으나 정말로 메서드여야 합니다.
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>해결 방법 #2: 대상 코드를 통해 디버거에 확인 중단 요청
 
오류 메시지는 디버거가 호출하려고 시도한 함수의 이름을 알려줍니다. 속성 getter 또는 ToString 메서드가 제대로 실행되지 않는 경우가 있으면, 특히 코드를 실행하려면 다른 스레드가 있어야 하는 코드가 문제인 경우에는 구현 함수가 `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency`를 호출하여 디버거에 함수 확인 중단을 요청할 수 있습니다. 이 해결 방법을 사용하면 계속 해당 함수를 명시적으로 확인할 수 있지만 기본 동작은 NotifyOfCrossThreadDependency 호출이 발생하면 실행이 중지되는 것입니다.
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>해결 방법 #3: 모든 암시적 확인 사용 안 함
 
이전 해결 방법으로 문제가 해결되지 않는 경우 *도구* / *옵션*으로 이동하여 *디버깅* / *일반* / *속성 확인 및 기타 암시적 함수 호출 사용* 설정을 선택 취소합니다. 이렇게 하면 대부분의 암시적 함수 확인이 사용하지 않도록 설정되며 문제가 해결됩니다.

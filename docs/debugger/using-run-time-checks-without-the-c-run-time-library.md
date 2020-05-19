---
title: C 런타임 라이브러리 없이 런타임 검사 사용 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 029aafa634ba0e6837cdc7d4304d0419420dd912
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728659"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>C 런타임 라이브러리 없이 런타임 검사 사용
C 런타임 라이브러리( **/NODEFAULTLIB** 사용)를 사용하지 않고 프로그램을 연결한 경우 런타임 검사 기능을 사용하려면 RunTmChk.lib에 연결해야 합니다.

`_RTC_Initialize`는 런타임 검사를 할 수 있도록 프로그램을 초기화합니다. C 런타임 라이브러리에 링크하지 않은 경우에는 다음과 같이 `_RTC_Initialize`를 호출하기 전에 런타임 오류 검사를 활성화한 상태에서 프로그램이 컴파일되었는지 확인해야 합니다.

```cpp
#ifdef __MSVC_RUNTIME_CHECKS
    _RTC_Initialize();
#endif
```

C 런타임 라이브러리에 링크하지 않은 경우에는 `_CRT_RTC_INITW`라는 함수도 정의해야 합니다. `_CRT_RTC_INITW`는 다음과 같이 사용자 정의 함수를 기본 오류 보고 함수로 설정합니다.

```cpp
// C version:
_RTC_error_fnW __cdecl _CRT_RTC_INITW(
        void *res0, void **res1, int res2, int res3, int res4)
{
    // set the error handler.
    return &MyErrorFunc;
}

// C++ version:
extern "C" _RTC_error_fnW __cdecl _CRT_RTC_INITW(
       void *res0, void **res1, int res2, int res3, int res4)
{
    // set the error handler:
    return &MyErrorFunc;
}
```

기본 오류 보고 함수를 설정한 후 `_RTC_SetErrorFuncW`를 사용하여 추가 오류 보고 함수를 설정할 수 있습니다. 자세한 내용은 [_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw)를 참조하세요.

## <a name="see-also"></a>참조
[방법: 네이티브 런타임 검사 사용](../debugger/how-to-use-native-run-time-checks.md)

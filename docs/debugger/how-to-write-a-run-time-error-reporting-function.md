---
title: 런타임 오류 보고 함수 작성 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, reporting functions
- reporting function
ms.assetid: 989bf312-5038-44f3-805f-39a34d18760e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 073943d8b6a3dbf5ee3af653a43046c3b389fbfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85348407"
---
# <a name="how-to-write-a-run-time-error-reporting-function-c"></a>방법: 런타임 오류 보고 함수 작성(C++)
사용자 지정 런타임 오류 보고 함수는 `_CrtDbgReportW`와 동일하게 선언해야 합니다. 이 함수는 디버거에 1을 값으로 반환해야 합니다.

다음 예제에서는 사용자 지정 보고 함수를 정의하는 방법을 보여 줍니다.

## <a name="example"></a>예제

```cpp
#include <stdio.h>
int errorhandler = 0;
void configureMyErrorFunc(int i)
{
    errorhandler = i;
}

int MyErrorFunc(int errorType, const wchar_t *filename,
                int linenumber, const wchar_t *moduleName,
                const wchar_t *format, ...)
{
    switch (errorhandler)
    {
    case 0:
    case 1:
        wprintf(L"Error type %d at %s line %d in %s",
                errorType, filename, linenumber, moduleName);
        break;
    case 2:
    case 3:
        fprintf(stderr, "Error type");
        break;
    }

    return 1;
}
```

## <a name="example"></a>예제
다음 예제는 좀 더 복잡한 사용자 지정 보고 함수를 보여 줍니다. 이 예제에서 switch 문은 `reportType`의 `_CrtDbgReportW` 매개 변수에서 정의한 여러 가지 오류 형식을 처리합니다. `_CrtDbgReportW`를 바꾸는 것이므로 `_CrtSetReportMode`는 사용할 수 없습니다. 사용자 지정 함수에서 출력을 처리해야 합니다. 이 함수의 첫째 가변 인수는 런타임 오류 번호를 사용합니다. 자세한 내용은 [_RTC_SetErrorType](/cpp/c-runtime-library/reference/rtc-seterrortype)을 참조하세요.

```cpp
#include <windows.h>
#include <stdarg.h>
#include <rtcapi.h>
#include <malloc.h>
#pragma runtime_checks("", off)
int Catch_RTC_Failure(int errType, const wchar_t *file, int line,
                      const wchar_t *module, const wchar_t *format, ...)
{
    // Prevent re-entrance.
    static long running = 0;
    while (InterlockedExchange(&running, 1))
        Sleep(0);
    // Now, disable all RTC failures.
    int numErrors = _RTC_NumErrors();
    int *errors=(int*)_alloca(numErrors);
    for (int i = 0; i < numErrors; i++)
        errors[i] = _RTC_SetErrorType((_RTC_ErrorNumber)i, _RTC_ERRTYPE_IGNORE);

    // First, get the rtc error number from the var-arg list.
    va_list vl;
    va_start(vl, format);
    _RTC_ErrorNumber rtc_errnum = va_arg(vl, _RTC_ErrorNumber);
    va_end(vl);

    wchar_t buf[512];
    const char *err = _RTC_GetErrDesc(rtc_errnum);
    swprintf_s(buf, 512, L"%S\nLine #%d\nFile:%s\nModule:%s",
        err,
        line,
        file ? file : L"Unknown",
        module ? module : L"Unknown");
    int res = (MessageBox(NULL, buf, L"RTC Failed...", MB_YESNO) == IDYES) ? 1 : 0;
    // Now, restore the RTC errortypes.
    for(int i = 0; i < numErrors; i++)
        _RTC_SetErrorType((_RTC_ErrorNumber)i, errors[i]);
    running = 0;
    return res;
}
#pragma runtime_checks("", restore)
```

## <a name="example"></a>예제
`_RTC_SetErrorFuncW`를 사용하여 `_CrtDbgReportW` 대신 사용자 지정 함수를 설치합니다. 자세한 내용은 [_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw)를 참조하세요. `_RTC_SetErrorFuncW`의 반환 값은 이전 보고 함수이며 필요한 경우 이를 저장하고 복원할 수 있습니다.

```cpp
#include <rtcapi.h>
int main()
{
    _RTC_error_fnW oldfunction, newfunc;
    oldfunction = _RTC_SetErrorFuncW(&MyErrorFunc);
    // Run some code.
    newfunc = _RTC_SetErrorFuncW(oldfunction);
    // newfunc == &MyErrorFunc;
    // Run some more code.
}
```

## <a name="see-also"></a>참조
[네이티브 런타임 검사 사용자 지정](../debugger/native-run-time-checks-customization.md)

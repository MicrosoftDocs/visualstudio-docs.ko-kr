---
title: 보고서 매크로 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.macros
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2129db98293cef678527fb331992c6c5960d8f9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731382"
---
# <a name="macros-for-reporting"></a>보고서 매크로
디버깅을 위해 CRTDBG.H에 정의된 **_RPTn** 및 **_RPTFn** 매크로를 `printf` 문 대신 사용할 수 있습니다. **_DEBUG**가 정의되지 않으면 이 매크로는 자동으로 릴리스 빌드에서 사라지므로 **#ifdef**로 둘러쌀 필요가 없습니다.

|매크로|설명|
|-----------|-----------------|
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|메시지 문자열과 0을 네 개의 인수로 출력합니다. _RPT1부터 **_RPT4**까지는 메시지 문자열이 인수에 대해 printf 스타일의 서식 문자열로 사용됩니다.|
|**_RPTF0**, **_RPTF1**, **_RPTF2**, **_RPTF4**|**_RPTn**과 같지만 이러한 매크로는 해당 매크로가 있는 파일 이름과 줄 번호도 출력합니다.|

 다음 예제를 참조하세요.

```cpp
#ifdef _DEBUG
    if ( someVar > MAX_SOMEVAR )
        printf( "OVERFLOW! In NameOfThisFunc( ),
               someVar=%d, otherVar=%d.\n",
               someVar, otherVar );
#endif
```

 이 코드는 `someVar`과 `otherVar`의 값을 **stdout**로 출력합니다. 다음 `_RPTF2` 호출을 사용하여 동일한 값과 파일 이름, 줄 번호를 보고할 수 있습니다.

```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );
```

특정 애플리케이션에서 C 런타임 라이브러리와 함께 제공된 매크로가 제공하지 않는 디버그 보고가 필요한 경우가 있을 수 있습니다. 이 경우 요구 사항에 맞게 특별히 디자인된 매크로를 작성할 수 있습니다. 예를 들어 헤더 파일 중 하나에서 다음과 같은 코드를 포함하여 **ALERT_IF2** 매크로를 정의할 수 있습니다.

```cpp
#ifndef _DEBUG                  /* For RELEASE builds */
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)
#else                           /* For DEBUG builds   */
#define  ALERT_IF2(expr, msg, arg1, arg2) \
    do { \
        if ((expr) && \
            (1 == _CrtDbgReport(_CRT_ERROR, \
                __FILE__, __LINE__, msg, arg1, arg2))) \
            _CrtDbgBreak( ); \
    } while (0)
#endif
```

 **ALERT_IF2**를 한 번 호출하여 **printf** 코드의 모든 함수를 실행할 수 있습니다.

```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),
someVar=%d, otherVar=%d.\n", someVar, otherVar );
```

 대상에 따라 더 많거나 더 적은 정보를 보고하도록 사용자 지정 매크로를 쉽게 변경할 수 있습니다. 이 접근 방법은 디버깅 요구 사항이 변화할 때 특히 유용합니다.

## <a name="see-also"></a>참조
- [CRT 디버깅 기술](../debugger/crt-debugging-techniques.md)

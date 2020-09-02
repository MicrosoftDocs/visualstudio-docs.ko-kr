---
title: 보고서 매크로 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.macros
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e4aee33d571f95e24a359fa2bc7e12ae8d64eae0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431630"
---
# <a name="macros-for-reporting"></a>보고서 매크로
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

CRTDBG.H에 정의 된 **_RPTn**및 **_RPTFn** 매크로를 사용할 수 있습니다. H-디버깅을 위해 문 사용을 대체 합니다 `printf` . 이러한 매크로는 **_DEBUG** 정의 되지 않은 경우 릴리스 빌드에서 자동으로 사라지고 **#ifdef**s로 묶을 필요가 없습니다.  
  
|매크로|설명|  
|-----------|-----------------|  
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|메시지 문자열과 0을 네 개의 인수로 출력합니다. _RPT1부터 **_RPT4**까지는 메시지 문자열이 인수에 대해 printf 스타일의 서식 문자열로 사용됩니다.|  
|**_RPTF0**, **_RPTF1**, **_RPTF2**, **_RPTF4**|**_RPTn** 와 동일 하지만 이러한 매크로는 매크로가 위치한 파일 이름과 줄 번호를 출력 하기도 합니다.|  
  
 다음 예제를 참조하세요.  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 이 코드는 `someVar`과 `otherVar`의 값을 **stdout**로 출력합니다. 다음 `_RPTF2` 호출을 사용하여 동일한 값과 파일 이름, 줄 번호를 보고할 수 있습니다.  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 특정 애플리케이션에서 C 런타임 라이브러리와 함께 제공된 매크로가 없다는 디버그 보고가 필요할 경우, 필요에 맞게 특별히 디자인된 매크로를 작성할 수 있습니다. 예를 들어 헤더 파일 중 하나에서 다음과 같은 코드를 포함하여 **ALERT_IF2** 매크로를 정의할 수 있습니다.  
  
```  
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
  
 **ALERT_IF2** 에 대 한 한 번의 호출은이 항목의 시작 부분에 있는 **printf** 코드의 모든 기능을 수행할 수 있습니다.  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 사용자 지정 매크로를 보다 편리하게 변경하여 여러 대상에 다소간의 정보를 보고할 수 있기 때문에, 디버깅이 필요할 때 특히 유용한 방법입니다.  
  
## <a name="see-also"></a>관련 항목  
 [CRT 디버깅 기술](../debugger/crt-debugging-techniques.md)

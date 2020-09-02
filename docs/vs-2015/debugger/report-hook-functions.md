---
title: 보고서 후크 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- hooks, report
- _CrtDbgReport function
- debugger, report hook functions
- memory allocation, debug heap
- debugging [C++], hook functions
- _CrtSetReportHook function
- report hook functions
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0a492a1db8b65cad74d02cec0f43bf0c81461730
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687505"
---
# <a name="report-hook-functions"></a>보고서 후크 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[_CrtSetReportHook](https://msdn.microsoft.com/library/1ae7c64f-8c84-4797-9574-b59f00f7a509)를 사용하여 설치한 보고서 후크 함수는 [_CrtDbgReport](https://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc)가 디버그 보고서를 생성할 때마다 호출됩니다. 보고서 후크 함수를 사용하여 특정한 할당 형식에 맞게 보고서를 필터링할 수 있습니다. 보고서 후크 함수에는 다음과 같이 프로토타입이 있어야 합니다.  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 **_CrtSetReportHook**에 전달한 포인터는 CRTDBG.H에 정의된 대로 **_CRT_REPORT_HOOK** 형식입니다.  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 런타임 라이브러리가 후크 함수를 호출하면, *nRptType* 인수는 보고서의 범주( **_CRT_WARN**, **_CRT_ERROR** 또는 **_CRT_ASSERT**)를 포함하고, *szMsg*는 완전히 어셈블된 보고서 메시지 문자열에 대한 포인터를 포함하며, *retVal*은 보고서 생성 후에 `_CrtDbgReport`가 계속 정상적으로 실행되어야 할 것인지 또는 디버거를 시작해야 할 것인지 지정합니다. (*retVal* 값이 0이면 계속 실행하고 값이 1이면 디버거를 시작합니다.)  
  
 요청한 메시지를 후크가 완전히 처리하여 더 이상 보고할 필요가 없으면 **TRUE**를 반환해야 합니다. **FALSE**를 반환하면 `_CrtDbgReport`가 정상적으로 메시지를 보고합니다.  
  
## <a name="see-also"></a>관련 항목  
 [디버그 후크 함수 작성](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 샘플](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)

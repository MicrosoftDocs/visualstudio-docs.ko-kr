---
title: 할당 후크 및 C 런타임 메모리 할당 | Microsoft Docs
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
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8487972c237b9c2ba6bf2594ffc1df43fa0c63cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702432"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>할당 후크 및 C 런타임 메모리 할당
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

할당 후크 함수가 내부 메모리를 할당하는 C 런타임 라이브러리 함수를 호출하는 경우, C 런타임 라이브러리 함수가 내부적으로 만든 메모리 할당인 `_CRT_BLOCK` 블록을 명시적으로 무시한다는 점은 매우 중요한 제한입니다. 할당 후크 함수의 처음에 다음과 같은 코드를 포함하여 `_CRT_BLOCK` 블록을 무시할 수 있습니다.  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 할당 후크가 `_CRT_BLOCK` 블록을 무시하지 않으면 후크에서 호출한 모든 C 런타임 라이브러리 함수는 무한 루프에서 프로그램을 트래핑할 수 있습니다. 예를 들어, `printf`는 내부 할당을 만듭니다. 후크 코드가를 호출 하 `printf` 는 경우 생성 된 할당으로 인해 후크가 다시 호출 되므로 **printf** 를 다시 호출 하 고 스택이 오버플로 될 때까지 계속 호출 됩니다. `_CRT_BLOCK` 할당 작업을 보고해야 할 경우, 이러한 제한을 피하려면 형식 지정과 출력에 C 런타임 함수 대신 Windows API 함수를 사용해야 합니다. Windows API는 C 런타임 라이브러리 힙을 사용하지 않기 때문에 무한 루프에서 할당 후크를 트래핑하지 않습니다.  
  
 런타임 라이브러리 소스 파일을 검사하면 기본 할당 후크 함수 **CrtDefaultAllocHook**(**TRUE**만 반환)가 자체 별도 파일인 DBGHOOK.C에 있음을 알 수 있습니다. 애플리케이션의 **main** 함수보다 먼저 실행되는 런타임 시작 코드가 만든 할당에 대해서도 할당 후크를 호출하려면 [_CrtSetAllocHook](https://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d)를 사용하지 말고 사용자의 함수로 이 기본 함수를 대체합니다.  
  
## <a name="see-also"></a>관련 항목  
 [디버그 후크 함수 작성](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 샘플](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)

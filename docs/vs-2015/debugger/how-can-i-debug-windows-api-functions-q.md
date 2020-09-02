---
title: Windows API 함수를 어떻게 디버깅할 수 있습니까? | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.api
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8c5fd73eb64c79ac9476c0036b9f2d709294d178
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704589"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Windows API 함수를 어떻게 디버깅할 수 있습니까?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NT 기호가 로드된 Windows API 함수를 디버깅하려면 다음 작업을 수행해야 합니다.  
  
### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>NT 기호가 있는 Windows API 함수에 중단점을 설정하려면  
  
- 함수가 상주하는 DLL 이름과 함수 이름을 함께 입력합니다. 32비트 코드에서는 함수 이름의 데코레이트된 형식을 사용합니다. 예를 들어 **MessageBeep**에 중단점을 설정하려면 다음을 입력해야 합니다.  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     데코레이트된 이름을 가져오려면 [데코레이트된 이름 보기](https://msdn.microsoft.com/f79e2717-a4db-4d12-a689-69830cce2be0)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [네이티브 코드 디버그 Faq](../debugger/debugging-native-code-faqs.md)   
 [네이티브 코드 디버그](../debugger/debugging-native-code.md)

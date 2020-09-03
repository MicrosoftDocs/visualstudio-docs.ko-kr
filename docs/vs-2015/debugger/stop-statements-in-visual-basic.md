---
title: Visual Basic의 Stop 문 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f2749ef9a6cfd310da5da832a283b55b6af59a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198885"
---
# <a name="stop-statements-in-visual-basic"></a>Visual Basic의 Stop 문
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

중단점을 설정하는 대신 Visual Basic의 Stop 문을 사용하는 프로그래밍 방식을 제공합니다. 디버거에서는 Stop 문이 나올 경우 프로그램 실행을 중단하여 중단 모드를 시작합니다. C# 프로그래머는 System.Diagnostics.Debugger.Break에 대한 호출을 사용하여 동일한 결과를 얻을 수 있습니다.  
  
 Stop 문을 설정하거나 제거하려면 소스 코드를 편집해야 합니다. 중단점을 설정하거나 제거하는 것처럼 디버거 명령을 사용하여 Stop 문을 설정하거나 제거할 수는 없습니다.  
  
 End 문과 달리, Stop 문은 변수를 다시 설정하거나 사용자를 디자인 모드로 되돌리지 않습니다. 디버그 메뉴에서 계속을 선택하면 계속 애플리케이션을 실행할 수 있습니다.  
  
 디버거 외부에서 Visual Basic 애플리케이션을 실행할 경우, Just-in-Time 디버깅이 활성화되면 Stop 문이 디버거를 실행합니다. Just-in-Time 디버깅이 활성화되지 않으면, Stop 문이 실행을 종료하는 End 문처럼 동작합니다. QueryUnload 이벤트나 Unload 이벤트가 발생하지 않으므로, Visual Basic 애플리케이션의 릴리스 버전에서 모든 Stop 문을 제거해야 합니다. 자세한 내용은 [Just-In-Time 디버깅](../debugger/just-in-time-debugging-in-visual-studio.md)을 참조하세요.  
  
 다음과 같은 조건부 컴파일을 사용하면 이 경우에 Stop 문을 제거하지 않아도 됩니다.  
  
```  
#If DEBUG Then  
   Stop  
#Else  
   ' Don't stop  
#End If  
```  
  
 또 다른 방법은 Stop 문 대신 Assert 문을 사용하는 것입니다. Debug.Assert 문은 지정된 조건이 충족되지 않을 경우에만 실행을 중단하고, 릴리스 버전을 빌드하면 자동으로 제거됩니다. 자세한 내용은 [관리 코드의 어설션](../debugger/assertions-in-managed-code.md)을 참조하세요. 디버그 버전에서 Assert 문이 항상 실행을 중단하도록 하려면 다음과 같이 지정하십시오.  
  
```  
Debug.Assert(false)  
```  
  
 다음과 같이 Debug.Fail 메서드를 사용할 수도 있습니다.  
  
```  
Debug.Fail("a clever output string goes here")  
```  
  
## <a name="see-also"></a>관련 항목  
 [디버거 보안](../debugger/debugger-security.md)   
 [C #, F # 및 Visual Basic 프로젝트 형식](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [관리 코드 디버그](../debugger/debugging-managed-code.md)

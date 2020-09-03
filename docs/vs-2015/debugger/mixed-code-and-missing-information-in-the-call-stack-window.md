---
title: 호출 스택 창의 혼합 코드 및 누락된 정보 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3995e14379fa4bd3ebd5cc276613c288b4437d35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193283"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>호출 스택 창의 혼합 코드 및 누락된 정보
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

관리 코드에 대한 호출 스택과 네이티브 코드에 대한 호출 스택은 서로 다르기 때문에 코드 형식이 혼합된 경우 디버거에서 전제 호출 스택이 표시되지 않을 수 있습니다. 네이티브 코드가 관리 코드를 호출하면 **호출 스택** 창이 다음과 같이 변경될 수 있습니다.  
  
- 관리 코드 바로 위의 네이티브 프레임이 **호출 스택** 창에서 없어질 수 있습니다. 자세한 내용은 [방법: 호출 스택 창에 네이티브 프레임이 없을 때 관리 코드에서 나가기](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md)를 참조하세요.  
  
- 디버거 외부에서 실행된 혼합 모드 애플리케이션의 경우, **호출 스택** 창에 관리 코드만 표시될 수 있으며 네이티브 프레임은 표시되지 않습니다.  
  
  두 경우 모두 아주 드문 경우입니다. 관리 코드에 대한 대부분의 네이티브 호출에서는 호출 스택이 올바르게 나타납니다.  
  
## <a name="see-also"></a>관련 항목  
 [방법: 호출 스택 창 사용](../debugger/how-to-use-the-call-stack-window.md)

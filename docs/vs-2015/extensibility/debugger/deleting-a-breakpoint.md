---
title: 중단점 삭제 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42cd353c216c21d14c4f6592da809c72acdba664
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841799"
---
# <a name="deleting-a-breakpoint"></a>중단점 삭제
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

다음은 보류 중인 중단점을 삭제 하는 프로세스에 대 한 설명입니다.  
  
## <a name="deletion-process"></a>삭제 프로세스  
 [IDebugPendingBreakpoint2::D e)](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) 메서드를 호출 하 여 보류 중인 중단점과 여기에서 바인딩된 모든 바인딩된 중단점을 제거 합니다.  
  
> [!NOTE]
> [IDebugBoundBreakpoint2::D e)](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)를 호출 하 여 단일 바인딩된 중단점을 삭제할 수도 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)

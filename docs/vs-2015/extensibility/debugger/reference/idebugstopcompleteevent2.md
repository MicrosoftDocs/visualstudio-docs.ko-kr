---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9c2a6a6e69bf47751706710801dd78c832ccd2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546925"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

디버그 엔진 (DE)은 프로그램이 중지 될 때이 선택적 이벤트를 세션 디버그 관리자 (SDM)로 보낼 수 있습니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 의 새 인터페이스입니다 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] . 이전 릴리스에서는 비동기 중지를 지원 하지 않았습니다.  
  
 [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) 은 다중 프로세스 또는 다중 프로그램 시나리오에서 SDM에 의해 호출 됩니다. 한 프로그램에서 SDM로 중지 이벤트를 보내면 SDM은 다른 프로그램을 중지 하도록 요청 합니다.  
  
 프로그램이 중지 되었음을 SDM에 게 비동기적으로 알리는 데 사용 됩니다. 이는 디버깅 된 프로그램 내에서 코드가 실행 되지 않는 경우를 동기적으로 완료할 [수 없도록 인터프리터](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) 디버그 엔진에 유용 합니다. 디버그 엔진이이 비동기 알림을 사용 하려는 경우 `S_ASYNC_STOP` [중지](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)에서 반환 해야 합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

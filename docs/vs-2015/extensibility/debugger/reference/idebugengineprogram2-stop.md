---
title: 'IDebugEngineProgram2:: Stop | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb74cb2940a91bbc64fa4a06f28d07a828357fc6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431487"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 프로그램에서 실행 중인 모든 스레드를 중지 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Stop(   
   void   
);  
```  
  
```csharp  
int Stop();  
```  
  
## <a name="return-value"></a>Return Value  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는이 프로그램이 다중 프로그램 환경에서 디버깅 될 때 호출 됩니다. 다른 프로그램의 중지 이벤트를 수신 하면이 메서드가이 프로그램에서 호출 됩니다. 이 메서드의 구현은 비동기 여야 합니다. 즉,이 메서드가 반환 되기 전에 모든 스레드를 중지 해야 하는 것은 아닙니다. 이 메서드의 구현은이 프로그램에서 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) 메서드를 호출 하는 것 처럼 간단할 수 있습니다.  
  
 이 메서드에 대 한 응답으로 디버그 이벤트를 보내지 않습니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)

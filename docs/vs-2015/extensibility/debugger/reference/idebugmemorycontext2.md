---
title: IDebugMemoryContext2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f5a0533e2f7ce50dce7ccdf1285e4ab28a4b7a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146363"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 디버그 중인 프로그램을 실행 하는 컴퓨터의 주소 공간에서 위치를 나타냅니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugMemoryContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 디버그 엔진 (DE)은 메모리의 주소를 나타내기 위해이 인터페이스를 구현 합니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 [Getmemorycontext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) 또는 [getmemorycontext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) 를 호출 하면이 인터페이스가 반환 됩니다. 또한 [더하기](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) 및 [빼기](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) 를 호출 하면 적절 한 산술 연산이 적용 된 후이 인터페이스의 새 복사본이 반환 됩니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDebugMemoryContext2` .  
  
|메서드|설명|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|이 컨텍스트의 사용자가 표시할 때 사용할 이름을 가져옵니다.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|이 컨텍스트를 설명 하는 정보를 가져옵니다.|  
|[추가](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|지정 된 값을 현재 컨텍스트의 주소에 추가 하 여 새 컨텍스트를 만듭니다.|  
|[빼기](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|현재 컨텍스트의 주소에서 지정 된 값을 빼서 새 컨텍스트를 만듭니다.|  
|[비교](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|비교 플래그에 지정 된 방식으로 두 컨텍스트를 비교 합니다.|  
  
## <a name="remarks"></a>설명  
 Visual Studio의 **메모리** 창은 [getmemorycontext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) 를 호출 하 여 `IDebugMemoryContext2` 메모리 주소에 사용 되는 계산 된 식이 포함 된 인터페이스를 가져옵니다. 이 컨텍스트는 [readat](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) 및 [writeat](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) 에 전달 되어 읽거나 쓸 주소를 지정 합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)   
 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)   
 [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)

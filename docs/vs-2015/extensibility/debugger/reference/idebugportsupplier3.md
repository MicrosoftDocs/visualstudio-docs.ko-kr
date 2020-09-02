---
title: IDebugPortSupplier3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e4ece720cf6880bba528dee99cdbdeb25c10087a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65674125"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

호출자는이 인터페이스를 사용 하 여 디버거 호출 사이에서 포트 공급자가 포트를 디스크에 기록 하 여 유지할 수 있는지 여부를 확인 한 다음 해당 유지 포트의 목록을 가져올 수 있습니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 사용자 지정 포트 공급자는이 인터페이스를 구현 하 여 포트 정보를 디스크에 유지 하거나 저장 하는 기능을 지원 합니다. 이 인터페이스는 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) 인터페이스와 동일한 개체에서 구현 되어야 합니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 인터페이스에서 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) `IDebugPortSupplier2` 를 호출 하 여이 인터페이스를 가져옵니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) 인터페이스에서 상속 된 메서드 외에도이 인터페이스는 다음을 지원 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|포트 공급자가 디버거 호출 사이에 포트를 디스크에 기록 하 여 유지할 수 있는지 여부를 반환 합니다.|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|이 포트 공급자가 디스크에 쓴 모든 포트를 열거 하는 데 사용할 수 있는 개체를 반환 합니다.|  
  
## <a name="remarks"></a>설명  
 포트 공급자가 호출에서 포트를 유지할 수 있는 경우이 인터페이스를 구현 해야 합니다. 포트 공급자가 인스턴스화될 때 포트를 로드 하 고 포트 공급자가 제거 되 면 디스크에 씁니다.  
  
 디버그 엔진은 일반적으로 포트 공급자와 상호 작용 하지 않으며이 인터페이스를 사용 하지 않습니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)

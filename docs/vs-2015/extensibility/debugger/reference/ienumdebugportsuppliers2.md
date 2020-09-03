---
title: IEnumDebugPortSuppliers2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f8ed12c0ba9c6263968c51a7e8cfcdfe2fe47011
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179159"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 포트 공급자를 열거 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugPortSuppliers2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 Visual Studio는이 인터페이스를 구현 하 여 포트 공급자 목록을 나타냅니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 [Enumportsuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) 를 호출 하 여 포트 공급자 목록을 가져옵니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IEnumDebugPortSuppliers2` .  
  
|메서드|설명|  
|------------|-----------------|  
|[다음](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|열거 시퀀스에서 지정 된 수의 포트 공급자를 검색 합니다.|  
|[skip](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|열거 시퀀스에서 지정 된 수의 포트 공급자를 건너뜁니다.|  
|[재설정](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|열거형 시퀀스를 시작 부분으로 다시 설정 합니다.|  
|[복제](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|현재 열거자와 동일한 열거 상태를 포함 하는 열거자를 만듭니다.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|열거자의 포트 공급자 수를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 디버그 엔진은 일반적으로이 인터페이스를 가져올 필요가 없습니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)

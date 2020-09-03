---
title: IDebugFunctionPosition2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4811a6f2aa79e2e19524c0ea1e3e687cd7e28220
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180910"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 소스 문서에 있는 함수의 추상 위치를 나타냅니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugFunctionPosition2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 디버그 엔진 (DE)은이 인터페이스를 구현 하 여 소스 문서 내의 함수 위치를 나타냅니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 이 인터페이스는 보류 중인 중단점을 만드는 데 사용 되는 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 구조체의 일부인 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 공용 구조체 (특히 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) 구조체)의 일부로 제공 됩니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDebugFunctionPosition2` .  
  
|메서드|설명|  
|------------|-----------------|  
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|이 위치가 상대적인 함수의 이름을 가져옵니다.|  
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|함수의 시작 부분에서 오프셋을 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 이 인터페이스에서 나타내는 위치는 텍스트 기반 이며 특히 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 구조체입니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)

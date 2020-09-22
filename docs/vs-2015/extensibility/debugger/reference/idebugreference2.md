---
title: IDebugReference2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac7e825bd33c184d580ada96843366f6d1627f22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841439"
---
# <a name="idebugreference2"></a>IDebugReference2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 스택 프레임 속성이 나 일부 다른 속성에 대 한 참조를 나타냅니다.  
  
> [!NOTE]
> `IDebugReference2` 는 나중에 사용 하도록 예약 되어 있으며 모든 메서드는를 반환 해야 `E_NOTIMPL` 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 DE는 특정 종류의 값에 대 한 참조를 나타내기 위해이 인터페이스를 구현 합니다. 예를 들어 값은 식 계산의 결과로 숫자 값, 메모리를 표시 하는 데 사용 되는 메모리 컨텍스트, 레지스터 및 해당 값 목록 일 수 있습니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 [Getreference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) 를 호출 하 여이 인터페이스를 가져옵니다. [Getparent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) 및 [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) 도이 인터페이스를 반환 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDebugReference2` .  
  
|메서드|Description|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|이 참조를 설명 하는 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 구조체를 가져옵니다.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|문자열에서이 참조의 값을 설정 합니다.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|다른 참조에서이 참조의 값을 설정 합니다.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|이 참조의 자식을 열거 합니다.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|이 참조의 부모를 가져옵니다.|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|이 참조의 가장 많이 파생 된 참조를 가져옵니다.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|이 참조에서 참조 하는 메모리 바이트를 가져옵니다.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|이 참조에 대 한 메모리 컨텍스트를 가져옵니다.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|이 참조의 크기 (바이트)를 가져옵니다.|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|이 참조 형식을 설정 합니다.|  
|[비교](../../../extensibility/debugger/reference/idebugreference2-compare.md)|이 참조를 다른 참조와 비교 합니다.|  
  
## <a name="remarks"></a>설명  
  
> [!NOTE]
> 이러한 엔터티를 나타낼 수 있지만 "속성"을 사용 하면 클래스의 멤버 변수를 의미 하는 것과 혼동 해서는 안 됩니다 `IDebugReference2` .  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 는 속성을 나타내며,는 속성 `IDebugReference2` 에 대 한 참조, 일반적으로 디버깅 중인 프로그램의 개체에 대 한 참조를 나타냅니다.  
  
 속성과 참조의 주요 차이점은 속성은 개체의 명명 된 인스턴스를 참조 하는 반면 참조는 명명 되지 않은 인스턴스를 참조 한다는 것입니다. 예를 들어 속성은에 의해 프로그램의 힙에서 개체를 참조할 수 있습니다 `"a.b"` . 다른 속성은와 같은 개체를 참조할 수 있습니다 `"c.d"` . 이 속성을 참조 하는 방법에는 `"a.b"` 또는 `"c.d"` 범위 안에 있어야 합니다. 동일한 개체에 대 한 참조는 이름이 없습니다. 개체에 대 한 메모리가 유효한 경우 개체를 참조할 수 있습니다.  
  
 `IDebugProperty2`인터페이스는 이름, 형식 및 주소를 사용 하는 값으로 간주할 수 있습니다. 반면에는 `IDebugReference2` 형식 및 주소로 간주할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)

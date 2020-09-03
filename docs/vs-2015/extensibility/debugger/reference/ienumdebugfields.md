---
title: IEnumDebugFields | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5e3c9a43b6903522fe2caf0e329f8e8faa69cd6b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161086"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스를 구현 하는 개체의 컬렉션을 나타냅니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugFields : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 이 인터페이스는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스를 구현 하는 개체 집합을 제공 하기 위해 기호 공급자에 의해 구현 됩니다. 이는 [Getcount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) 메서드가 있으므로 표준 COM 열거형이 아닙니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 이 인터페이스는 [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) 및 [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)에 의해 반환 됩니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 이 인터페이스는 다음 메서드를 구현 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[다음](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|열거형에서 다음 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 개체 집합을 검색 합니다.|  
|[skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|지정 된 수의 항목을 건너뜁니다.|  
|[재설정](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|열거형을 첫 번째 항목으로 다시 설정 합니다.|  
|[복제](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|현재 열거형의 복사본을 검색 합니다.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|열거형의 항목 수를 검색 합니다.|  
  
## <a name="remarks"></a>설명  
  
## <a name="requirements"></a>요구 사항  
 헤더: sh  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)   
 [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)

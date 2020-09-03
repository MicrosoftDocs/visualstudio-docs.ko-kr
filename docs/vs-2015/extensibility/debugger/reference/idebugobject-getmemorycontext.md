---
title: 'IDebugObject:: GetMemoryContext | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::GetMemoryContext
helpviewer_keywords:
- IDebugObject::GetMemoryContext method
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5e69e5a77e93df2d338eb7d2e7114129ea9ac8d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162457"
---
# <a name="idebugobjectgetmemorycontext"></a>IDebugObject::GetMemoryContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

개체의 값 주소를 나타내는 메모리 컨텍스트를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetMemoryContext(   
   IDebugMemoryContext2** pContext  
);  
```  
  
```csharp  
int GetMemoryContext(  
   ref IDebugMemoryContext2 pContext  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pContext`  
 제한이 개체의 값 주소를 나타내는 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 개체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 반환 된 메모리 컨텍스트는이 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 개체가 나타내는 값의 주소를 지정 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

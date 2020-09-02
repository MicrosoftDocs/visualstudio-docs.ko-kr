---
title: 'IDebugMemoryContext2:: 빼기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2efe4e15c5489ef07741a0d267b9c1b870d07aa8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146366"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

현재 컨텍스트에서 지정 된 값을 빼고 새 컨텍스트를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Subtract(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int Subtract(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwCount`  
 진행 감소 시킬 메모리 바이트의 수입니다.  
  
 `ppMemCxt`  
 제한이 새 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 개체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 메모리 컨텍스트는 주소 이므로 주소에서 값을 빼면 새 컨텍스트 인터페이스가 필요한 새 주소가 생성 됩니다.  
  
 결과 주소가이 컨텍스트와 연결 된 메모리 공간을 벗어난 경우에도이 메서드는 항상 새 컨텍스트를 생성 해야 합니다. 이에 대 한 유일한 예외는 새 컨텍스트에 대해 메모리를 할당할 수 없는 경우이 고 `ppMemCxt` 가 null 값 (오류) 인 경우입니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

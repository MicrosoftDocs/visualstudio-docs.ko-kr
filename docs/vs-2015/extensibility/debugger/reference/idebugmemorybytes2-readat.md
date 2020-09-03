---
title: 'IDebugMemoryBytes2:: ReadAt | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f10dc6e9e00e2b7f66722f3c89b74bb14e45fdbe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180586"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

지정 된 위치에서 시작 하 여 바이트 시퀀스를 읽습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```csharp  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pStartContext`  
 진행 바이트 읽기를 시작할 위치를 지정 하는 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 개체입니다.  
  
 `dwCount`  
 진행 읽을 바이트 수입니다. 또한 배열의 길이를 지정 합니다 `rgbMemory` .  
  
 `rgbMemory`  
 [in, out] 실제로 읽은 바이트를 사용 하 여 채워진 배열입니다.  
  
 `pdwRead`  
 제한이 실제로 읽은 연속 바이트 수를 반환 합니다.  
  
 `pdwUnreadable`  
 [in, out] 읽을 수 없는 바이트 수를 반환 합니다. 클라이언트가 읽을 수 없는 바이트 수를 uninterested 경우 null 값이 될 수 있습니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 100 바이트를 요청 하 고 첫 번째 50를 읽을 수 있는 경우 다음 20 개를 읽을 수 없으며 나머지 30 개를 읽을 수 있습니다 .이 메서드는 다음을 반환 합니다.  
  
 *`pdwRead` = 50  
  
 *`pdwUnreadable` = 20  
  
 이 경우 `*pdwRead + *pdwUnreadable < dwCount` 호출자는 요청 된 원래 100의 남은 30 바이트를 읽도록 추가 호출을 수행 해야 하며 매개 변수에 전달 된 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 개체는 `pStartContext` 70로 고급 이어야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

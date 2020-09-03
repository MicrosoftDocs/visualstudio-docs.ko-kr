---
title: 'IDebugMemoryBytes2:: GetSize | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::GetSize
helpviewer_keywords:
- IDebugMemoryBytes2::GetSize method
- GetSize method
ms.assetid: dae64c5f-5b54-40c3-b32f-ec3b16c093f7
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0e4a1772b4cba1863a0e3d93b269e827f4d00568
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180559"
---
# <a name="idebugmemorybytes2getsize"></a>IDebugMemoryBytes2::GetSize
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) 개체가 나타내는 메모리의 크기 (바이트)를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetSize(   
   UINT64* pqwSize  
);  
```  
  
```csharp  
int GetSize(  
   out ulong pqwSize  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pqwSize`  
 제한이 메모리 공간의 크기 (바이트)를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)

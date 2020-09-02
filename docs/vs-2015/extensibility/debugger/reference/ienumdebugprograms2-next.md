---
title: 'IEnumDebugPrograms2:: Next | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Next
helpviewer_keywords:
- IEnumDebugPrograms2::Next
ms.assetid: 9120e263-e97c-4a40-ab2c-e9264ce3d6c4
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 356f1086c4490c45672c5f71e761bdfc6cbe762d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199591"
---
# <a name="ienumdebugprograms2next"></a>IEnumDebugPrograms2::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

열거형에서 다음 요소 집합을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Next(  
   ULONG            celt,  
   IDebugProgram2** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint             celt,  
   IDebugProgram2[] rgelt,  
   ref uint         pceltFetched  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `celt`  
 진행 검색할 요소의 수입니다. 또한 배열의 최대 크기를 지정 합니다 `rgelt` .  
  
 `rgelt`  
 [in, out] 채워질 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 요소의 배열입니다.  
  
 `pceltFetched`  
 제한이 에서 실제로 반환 된 요소의 수를 반환 합니다 `rgelt` .  
  
## <a name="return-value"></a>반환 값  
 성공하면 `S_OK`를 반환합니다. `S_FALSE`요청 된 수의 요소를 반환할 수 있으면를 반환 하 고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

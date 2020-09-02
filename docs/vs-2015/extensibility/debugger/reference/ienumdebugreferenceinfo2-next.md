---
title: 'IEnumDebugReferenceInfo2:: Next | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2::Next
helpviewer_keywords:
- IEnumDebugReferenceInfo2::Next
ms.assetid: 70b31a57-1701-4757-9e7e-63ec60a71b3c
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 382587a351cebb7bb836759c1e6e994ea435057c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147804"
---
# <a name="ienumdebugreferenceinfo2next"></a>IEnumDebugReferenceInfo2::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

열거형에서 다음 요소 집합을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Next(  
   ULONG                   celt,  
   DEBUG_REFERENCE_INFO ** rgelt,  
   ULONG*                  pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint                   celt,  
   DEBUG_REFERENCE_INFO[] rgelt,  
   ref uint               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `celt`  
 진행 검색할 요소의 수입니다. 또한 배열의 최대 크기를 지정 합니다 `rgelt` .  
  
 `rgelt`  
 [in, out] 채워질 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 요소의 배열입니다.  
  
 `pceltFetched`  
 제한이 에서 실제로 반환 된 요소의 수를 반환 합니다 `rgelt` .  
  
## <a name="return-value"></a>반환 값  
 성공하면 `S_OK`를 반환합니다. `S_FALSE`요청 된 수의 요소를 반환할 수 있으면를 반환 하 고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)

---
title: 'IDebugObject:: GetSize | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::GetSize
helpviewer_keywords:
- IDebugObject::GetSize method
ms.assetid: 89af423b-36eb-479d-b2de-2693455eca15
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ffafe6b62047a577b2bfce74c8462d9051c4dcfb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192274"
---
# <a name="idebugobjectgetsize"></a>IDebugObject::GetSize
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

개체의 크기 (바이트)를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetSize(   
   UINT* pnSize  
);  
```  
  
```csharp  
int GetSize(  
   out uint pnSize  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pnSize`  
 제한이 크기 (바이트)를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md) 메서드를 사용 하 여 값을 바이트 시퀀스로 검색 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)

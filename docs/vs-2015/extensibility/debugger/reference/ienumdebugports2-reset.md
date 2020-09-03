---
title: 'IEnumDebugPorts2:: Reset | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::Reset
helpviewer_keywords:
- IEnumDebugPorts2::Reset
ms.assetid: 67da406c-eadb-421e-ae12-e26e9866f262
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a59443b16b9c133744ee6a638e56c3850109061a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155061"
---
# <a name="ienumdebugports2reset"></a>IEnumDebugPorts2::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

열거형을 첫 번째 요소로 다시 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Return Value  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이 메서드가 호출 된 후 [다음](../../../extensibility/debugger/reference/ienumdebugports2-next.md) 메서드에 대 한 다음 호출에서 열거형의 첫 번째 요소를 반환 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)

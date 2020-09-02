---
title: 'IDebugProperty2:: GetDerivedMostProperty | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fde68c090de11d6b479ea0587843a3d4a9d21f94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164937"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

속성의 파생 속성 속성을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetDerivedMostProperty (   
   IDebugProperty2** ppDerivedMost  
);  
```  
  
```csharp  
int GetDerivedMostProperty (   
   out IDebugProperty2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppDerivedMost`  
 제한이 가장 많이 파생 된 속성을 나타내는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 개체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. `S_GETDERIVEDMOST_NO_DERIVED_MOST`검색할 파생 된 속성이 없으면를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 예를 들어이 속성이을 구현 하는 개체를 설명 `ClassRoot` 하지만 실제로에서 파생 되는의 인스턴스화 인 경우 `ClassDerived` `ClassRoot` 이 메서드는 개체를 설명 하는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 개체를 반환 합니다 `ClassDerived` .  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

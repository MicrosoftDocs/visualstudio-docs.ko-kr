---
title: 'IDebugFunctionObject:: CreateArrayObject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 53c1961eb1ed72580fc314d7a1542ddc926780f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205816"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

배열 개체를 만듭니다. 이 배열에는 기본 또는 개체 인스턴스 값이 포함 될 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT CreateArrayObject(   
   OBJECT_TYPE    ot,  
   IDebugField*   pClassField,  
   DWORD          dwRank,  
   DWORD          dwDims[],  
   DWORD          dwLowBounds[],  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateArrayObject(  
   enum_OBJECT_TYPE ot,   
   IDebugField      pClassField,   
   uint             dwRank,   
   uint[]           dwDims,   
   uint[]           dwLowBounds,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ot`  
 진행 새 배열 개체의 형식을 나타내는 [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) 열거형의 값을 지정 합니다.  
  
 `pClassField`  
 진행 개체 인스턴스 값의 배열을 만드는 경우 개체의 클래스를 나타내는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 개체입니다. 기본 개체의 배열을 만드는 경우이 매개 변수는 null 값입니다.  
  
 `dwRank`  
 진행 배열의 차원 수 또는 차수입니다.  
  
 `dwDims`  
 진행 배열의 각 차원 크기입니다.  
  
 `dwLowBounds`  
 진행 각 차원의 원본 (일반적으로 0 또는 1)입니다.  
  
 `ppObject`  
 제한이 새로 만든 배열을 나타내는 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 개체를 반환 합니다. 실제로 [Idebugarrayobject](../../../extensibility/debugger/reference/idebugarrayobject.md) 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 [Idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 인터페이스로 표현 되는 함수에 대 한 배열 매개 변수를 나타내는 개체를 만들려면이 메서드를 호출 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)

---
title: 'IDebugFunctionObject:: CreatePrimitiveObject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3531483c113c37587b253bed90a9985541b2e526
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179448"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

단순 정수와 같은 기본 데이터 개체를 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT CreatePrimitiveObject(   
   OBJECT_TYPE    ot,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreatePrimitiveObject(  
   enum_OBJECT_TYPE ot,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ot`  
 진행 만들 기본 형식을 나타내는 [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) 열거형의 값입니다.  
  
 `ppObject`  
 제한이 새로 만든 개체를 나타내는 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 [Idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 인터페이스로 표현 되는 함수에 대 한 매개 변수인 기본 개체를 나타내는 개체를 만들려면이 메서드를 호출 합니다. 예를 들어 식 문자열이 "myString (5)" 인 경우이 메서드는 정수 5를 나타내는 개체를 만드는 데 사용 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)

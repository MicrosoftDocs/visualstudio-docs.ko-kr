---
title: 'IDebugClassField:: GetEnclosingClass | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 896d3ecd5202bf85e6b9e86af31796c662a6eef1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191001"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 클래스를 포함 하는 클래스를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```csharp  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppClassField`  
 제한이 바깥쪽 클래스를 나타내는 [Idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) 개체를 반환 합니다. 바깥쪽 클래스가 없는 경우 null 값을 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 이 [Idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) 개체가 나타내는 클래스가 중첩 된 클래스인 경우 `ppClassField` 매개 변수는 `IDebugClassField` 바깥쪽 클래스를 나타내는 개체를 반환 합니다. 예를 들어, 다음 클래스 정의가 제공 됩니다.  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 `GetEnclosingClass`클래스를 나타내는 개체에서 메서드를 호출 하면 `IDebugClassField` `NestedClass` `IDebugClassField` 클래스를 나타내는 개체가 반환 `RootClass` 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)

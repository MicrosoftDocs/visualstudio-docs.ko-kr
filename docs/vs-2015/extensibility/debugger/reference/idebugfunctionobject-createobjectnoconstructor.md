---
title: 'IDebugFunctionObject:: CreateObjectNoConstructor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0ea00035eb220ccd08590ceaea6db98944f4657a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179456"
---
# <a name="idebugfunctionobjectcreateobjectnoconstructor"></a>IDebugFunctionObject::CreateObjectNoConstructor
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

생성자 없이 개체를 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT CreateObjectNoConstructor(   
   IDebugField*   pClassObject,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateObjectNoConstructor(  
   IDebugField      pClassField,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pClassObject`  
 진행 만들 개체의 형식을 나타내는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 개체입니다.  
  
 `ppObject`  
 제한이 새로 만든 개체를 나타내는 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 [Idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 인터페이스로 표현 되는 함수에 대 한 매개 변수인 구조체 또는 복합 형식의 인스턴스를 나타내는 개체를 만들려면이 메서드를 호출 합니다.  
  
 개체 매개 변수에 생성자가 필요한 경우 [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md) 메서드를 호출 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)

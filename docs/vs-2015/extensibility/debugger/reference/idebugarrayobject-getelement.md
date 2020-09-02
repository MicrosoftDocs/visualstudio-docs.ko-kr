---
title: 'IDebugArrayObject:: GetElement | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac59a14a2d3be06c9e1523bcdc0d0ad026e0a7d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423688"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

배열의 요소를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetElement(   
   DWORD          dwIndex,  
   IDebugObject** ppElement  
);  
```  
  
```csharp  
int GetElement(  
   [In] uint dwIndex,   
   out IDebugObject ppElement  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwIndex`  
 진행 요소 인덱스입니다.  
  
 `ppElement`  
 제한이 요소를 나타내는 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 배열 개체가 다차원 인 경우에도 배열 개체의 모든 요소를 1 차원 배열로 표시 합니다. 예를 들어, 배열 `myarray[3][2][6]` 및 `dwIndex` 매개 변수가 20 인 경우이 메서드는에서 요소를 반환 `myarray[1][1][2]` 하 고 `dwIndex` 21의 매개 변수는에서 요소를 반환 `myarray[1][1][3]` 합니다. [Getcount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) 메서드를 사용 하 여 배열에 있는 요소의 총 수를 확인 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)

---
title: 'IDebugMethodField:: EnumArguments | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5744e25f76676e70e25777596fb0d8eb3a580511
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205230"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

메서드를 호출 하는 데 필요한 각 인수의 형식에 대 한 열거자를 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT EnumArguments(   
   IEnumDebugFields** ppParams  
);  
```  
  
```csharp  
int EnumArguments(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppParams`  
 제한이 인수 형식 목록을 나타내는 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 개체를 반환 합니다. 인수가 없으면 null 값을 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 S_OK 반환 하거나 인수가 없는 경우 S_FALSE을 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.  
  
## <a name="remarks"></a>설명  
 각 요소는 각 매개 변수의 형식을 나타내는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 개체입니다. [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) 메서드를 호출 하 여 각 매개 변수의 형식에 대 한 정보를 검색 합니다.  
  
 형식과 함께 매개 변수 이름이 필요한 경우 [Enumparameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) 메서드를 호출 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)

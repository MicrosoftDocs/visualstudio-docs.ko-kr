---
title: 'IDebugClassField:: EnumInterfacesImplemented | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 45cdc4ea3d1dad911179ce7b2a4926248ee921fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191005"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 클래스에서 구현 하는 인터페이스에 대 한 열거자를 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT EnumInterfacesImplemented(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumInterfacesImplemented(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppEnum`  
 제한이 구현 된 인터페이스 목록을 나타내는 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 개체를 반환 합니다. 인터페이스가 없으면 null 값을 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 S_OK을 반환 하거나이 클래스에 구현 된 인터페이스가 없는 경우 S_FALSE을 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.  
  
## <a name="remarks"></a>설명  
 열거형의 각 요소는 인터페이스를 설명 하는 [Idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) 개체입니다. 비관리 코드는 [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] 인터페이스를 불연속 엔터티로 사용 하지 않으므로이 메서드는 항상 비관리 코드에 대해 null 값을 반환 [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)

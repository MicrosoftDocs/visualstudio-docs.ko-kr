---
title: 'IDebugDefaultPort2:: GetPortNotify | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c0f5b1faf000ef982e38736b3cd3ea89a1dc2dc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196277"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 메서드는이 포트에 대 한 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) 인터페이스를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetPortNotify(  
   IDebugPortNotify2** ppPortNotify  
);  
```  
  
```csharp  
int GetPortNotify(  
   out IDebugPortNotify2 ppPortNotify  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppPortNotify`  
 제한이 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 일반적으로 `QueryInterface` [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 인터페이스를 구현 하는 개체에서 메서드를 호출 하 여 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) 인터페이스를 가져옵니다. 그러나 원하는 인터페이스가 다른 개체에서 구현 되는 경우도 있습니다. 이 메서드는 이러한 상황을 숨기고 `IDebugPortNotify2` 가장 적절 한 개체에서 인터페이스를 반환 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)

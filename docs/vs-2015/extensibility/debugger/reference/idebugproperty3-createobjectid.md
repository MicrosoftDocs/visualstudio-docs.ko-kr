---
title: 'IDebugProperty3:: CreateObjectID | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0035faad9078acd70886d597f039c0d8de5ee12f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841482"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

는이 속성에 대 한 고유 ID를 만들어 다른 모든 속성에서 고유한 지 확인 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>Return Value  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 세션 디버그 관리자가이 속성이 다른 모든 속성에서 고유 하 게 식별 되는지 확인 하려고 할 때 호출 됩니다. 디버그 엔진 (DE)은 처리 하는 속성이 이미 고유 하 게 식별 되는 경우를 제외 하 고이 메서드를 지원 합니다. DE가이 메서드를 지원 하지 않는 경우를 반환 `E_NOTIMPL` 합니다.  
  
 를 사용 하 여 만든 모든 고유 ID `CreateObjectID` 는 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) 메서드를 호출할 때 제거 됩니다. 또한이 속성을 고유 하 게 식별 하는 데 필요한 필요성이 있음을 나타냅니다.  
  
> [!NOTE]
> 이 고유 ID를 검색할 수 있는 방법이 없으므로 DE는 메서드가 호출 될 때 고유한 Id에 대해 원하는 모든 작업을 수행할 수 있습니다 `CreateObjectID` .  
  
## <a name="see-also"></a>참고 항목  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)

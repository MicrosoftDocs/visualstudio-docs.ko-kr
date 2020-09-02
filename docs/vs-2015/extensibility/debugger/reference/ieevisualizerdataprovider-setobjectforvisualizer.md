---
title: 'IEEVisualizerDataProvider:: SetObjectForVisualizer 도우미 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d20164e31f8c42b7099f99ff34ac120319a2def1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62540281"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 메서드는 시각화 도우미가 나타내는 개체를 변경 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```csharp  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pNewObject`  
 진행 설정할 개체입니다.  
  
 `error`  
 제한이 개체를 설정 하는 동안 오류가 발생 한 경우이 문자열에는 오류 메시지가 포함 됩니다.  
  
 `pException`  
 제한이 오류가 발생 한 경우이 개체는 예외 정보를 포함 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 오류 정보가 반환 되는 방법을 결정 하는 것은 구현자의 결정입니다. 그러나 일부 호출자는 오류를 알 수 있도록 예외 개체가 반환 되었는지만 확인할 수 있으므로 오류가 발생 한 경우이 메서드는 항상 예외 개체를 반환 해야 합니다. 호출자가이를 사용 하려는 경우에도 오류 문자열을 제공 해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

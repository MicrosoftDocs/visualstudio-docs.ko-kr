---
title: 'IEEVisualizerDataProvider:: GetObjectForVisualizer | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::GetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::GetObjectForVisualizer method
ms.assetid: bd5376fc-13b4-40b7-9a5d-7ba8289f1b24
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88562ae2238f33f1f46913a42df44fcb482cc8fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192077"
---
# <a name="ieevisualizerdataprovidergetobjectforvisualizer"></a>IEEVisualizerDataProvider::GetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 메서드는이 시각화 도우미가 나타내는 개체를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetObjectForVisualizer(  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int GetObjectForVisualizer(  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppObject`  
 제한이 이 시각화 도우미가 나타내는 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 `GetObjectForVisualizer` 는 캐시 된 버전의 개체를 반환할 수 있습니다. 호출자가 개체가 최신 상태 인지 확인 하려는 경우 [Getnewobjectforvisualizer 도우미](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)를 호출 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetNewObjectForVisualizer 도우미](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

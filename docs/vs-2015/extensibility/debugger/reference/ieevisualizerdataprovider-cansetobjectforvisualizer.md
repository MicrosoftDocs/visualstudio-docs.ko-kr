---
title: 'IEEVisualizerDataProvider:: CanSetObjectForVisualizer 도우미 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::CanSetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::CanSetObjectForVisualizer method
ms.assetid: 70fd3c6f-2f82-43a3-993b-c1dc8aa080bf
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: af1569e315b2010ad734c8776bd8436110365c40
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196164"
---
# <a name="ieevisualizerdataprovidercansetobjectforvisualizer"></a>IEEVisualizerDataProvider::CanSetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 메서드는 시각화 도우미가 업데이트를 나타내는 데이터 개체를 가질 수 있는지 여부를 확인 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT CanSetObjectForVisualizer(  
   BOOL* b  
);  
```  
  
```csharp  
int CanSetObjectForVisualizer(  
   out int b  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `b`  
 제한이 `TRUE`시각화 도우미의 개체를 업데이트할 수 있는 경우 0이 아닌 값이 고, 그렇지 않으면 0 ( `FALSE` )입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 예를 들어 읽기 전용 메모리에 바인딩된 개체는 변경할 수 없습니다.  
  
## <a name="see-also"></a>관련 항목  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

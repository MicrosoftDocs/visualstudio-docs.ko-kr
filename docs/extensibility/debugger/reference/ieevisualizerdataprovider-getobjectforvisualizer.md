---
description: 이 메서드는이 시각화 도우미가 나타내는 개체를 가져옵니다.
title: 'IEEVisualizerDataProvider:: GetObjectForVisualizer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::GetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::GetObjectForVisualizer method
ms.assetid: bd5376fc-13b4-40b7-9a5d-7ba8289f1b24
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ec4cef6cf7a0715ee31ce5a88736581a0abd610b
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222915"
---
# <a name="ieevisualizerdataprovidergetobjectforvisualizer"></a>IEEVisualizerDataProvider::GetObjectForVisualizer
이 메서드는이 시각화 도우미가 나타내는 개체를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetObjectForVisualizer(
   IDebugObject** ppObject
);
```

```csharp
int GetObjectForVisualizer(
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>매개 변수
`ppObject`\
제한이 이 시각화 도우미가 나타내는 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 `GetObjectForVisualizer` 는 캐시 된 버전의 개체를 반환할 수 있습니다. 호출자가 개체가 최신 상태 인지 확인 하려는 경우 [Getnewobjectforvisualizer 도우미](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)를 호출 합니다.

## <a name="see-also"></a>참고 항목
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

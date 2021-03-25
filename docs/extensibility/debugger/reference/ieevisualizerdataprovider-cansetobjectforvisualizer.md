---
description: 이 메서드는 시각화 도우미가 업데이트를 나타내는 데이터 개체를 가질 수 있는지 여부를 확인 합니다.
title: 'IEEVisualizerDataProvider:: CanSetObjectForVisualizer 도우미 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::CanSetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::CanSetObjectForVisualizer method
ms.assetid: 70fd3c6f-2f82-43a3-993b-c1dc8aa080bf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 81d958bb7cb931f485f8efa807dc9d322bab1fa4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058185"
---
# <a name="ieevisualizerdataprovidercansetobjectforvisualizer"></a>IEEVisualizerDataProvider::CanSetObjectForVisualizer
이 메서드는 시각화 도우미가 업데이트를 나타내는 데이터 개체를 가질 수 있는지 여부를 확인 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CanSetObjectForVisualizer(
   BOOL* b
);
```

```csharp
int CanSetObjectForVisualizer(
   out int b
);
```

## <a name="parameters"></a>매개 변수
`b`\
제한이 `TRUE`시각화 도우미의 개체를 업데이트할 수 있는 경우 0이 아닌 값이 고, 그렇지 않으면 0 ( `FALSE` )입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 예를 들어 읽기 전용 메모리에 바인딩된 개체는 변경할 수 없습니다.

## <a name="see-also"></a>참조
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

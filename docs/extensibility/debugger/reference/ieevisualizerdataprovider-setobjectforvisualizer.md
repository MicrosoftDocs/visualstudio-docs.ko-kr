---
title: IEE비주얼라이저데이터제공자:SetObjectFor비주얼라이저 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab63f1e74e0cd3ac64a4d7e7687a9136075b41a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718084"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
이 메서드는 시각화 도우미가 나타내는 개체를 변경합니다.

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

## <a name="parameters"></a>매개 변수
`pNewObject`\
【인】 설정할 개체입니다.

`error`\
【아웃】 개체를 설정하는 데 오류가 있는 경우 이 문자열에는 오류 메시지가 표시됩니다.

`pException`\
【아웃】 오류가 있는 경우 이 개체는 예외 정보를 보유합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 오류 정보가 반환되는 방법을 결정하는 것은 구현자의 결정입니다. 그러나 일부 호출자는 예외 개체가 오류가 있음을 알리기 위해 반환되었는지 만 볼 수 있으므로 이 메서드는 오류가 있는 경우 항상 예외 개체를 반환해야 합니다. 호출자가 오류를 사용하려는 경우에도 오류 문자열을 제공해야 합니다.

## <a name="see-also"></a>참조
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

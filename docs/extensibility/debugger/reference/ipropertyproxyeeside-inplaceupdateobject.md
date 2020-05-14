---
title: IPropertyProxyEESide::인플레이스업데이트개체 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79167b0f7e8094fabf80bb9b2d83c94ac874aa31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714900"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
지정된 데이터 개체로 개체의 데이터를 업데이트하고 개체의 새 데이터를 나타내는 새 데이터 개체를 반환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT InPlaceUpdateObject(
   [in] IEEDataStorage*   dataIn,
   [out] IEEDataStorage** dataOut
);
```

```csharp
int InPlaceUpdateObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>매개 변수
`dataIn`\
【인】 새 데이터가 포함된 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 개체입니다.

`dataOut`\
【아웃】 대체된 `IEEDataStorage` 데이터가 포함된 새 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드는 실제로 개체의 데이터를 업데이트합니다. 반환된 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 개체의 데이터는 들어오는 `IEEDataStorage` 개체의 데이터와 같을 필요는 없지만 반환된 개체는 속성의 현재 값을 반영해야 합니다.

 들어오는 데이터 개체는 일반적으로 EE에 의해 구현되지 않습니다. 그러나 이 메서드에서 반환되는 개체는 항상 EE에 의해 구현되어 `IEEDataStorage` EE가 원하는 클래스에 대한 인터페이스를 구현할 수 있습니다.

 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) 메서드는 들어오는 데이터 개체를 기반으로 데이터 개체를 만들지만 속성의 원래 데이터에는 영향을 주지 않습니다.

## <a name="see-also"></a>참조
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)

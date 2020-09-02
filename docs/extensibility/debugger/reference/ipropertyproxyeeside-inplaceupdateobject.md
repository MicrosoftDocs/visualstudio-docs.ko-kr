---
title: 'IPropertyProxyEESide:: InPlaceUpdateObject | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714900"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
지정 된 데이터 개체를 사용 하 여 개체의 데이터를 업데이트 하 고 개체의 새 데이터를 나타내는 새 데이터 개체를 반환 합니다.

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
진행 새 데이터를 포함 하는 [Ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) 개체입니다.

`dataOut`\
제한이 `IEEDataStorage` 대체 된 데이터를 포함 하는 새 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 실제로 개체의 데이터를 업데이트 합니다. 반환 된 [Ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) 개체의 데이터는 들어오는 개체의 데이터와 동일할 필요는 `IEEDataStorage` 없지만 반환 되는 개체는 속성의 현재 값을 반영 해야 합니다.

 들어오는 데이터 개체는 일반적으로 EE에서 구현 하지 않습니다. 그러나이 메서드에서 반환 하는 개체는 항상 EE에서 구현 되므로 EE에서 `IEEDataStorage` 원하는 클래스에 대해 인터페이스를 구현할 수 있습니다.

 [Creatreing ementobject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) 메서드는 들어오는 데이터 개체를 기반으로 데이터 개체를 만들지만 속성의 원래 데이터에는 영향을 주지 않습니다.

## <a name="see-also"></a>추가 정보
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)

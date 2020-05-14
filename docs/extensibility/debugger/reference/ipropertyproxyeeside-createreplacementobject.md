---
title: IPropertyProxyESide::만들기대체 개체 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f449a505c56c180f1bab021007f1b635a2461996
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715044"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
식 계산기(EE)와 관련된 데이터 개체의 복사본을 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CreateReplacementObject(
   IEEDataStorage*  dataIn,
   IEEDataStorage** dataOut
);
```

```csharp
int CreateReplacementObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>매개 변수
`dataIn`\
【인】 복사할 데이터를 보유하는 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 개체입니다.

`dataOut`\
【아웃】 새 `IEEDataStorage` 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드에는 바이트 배열을 나타내는 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 개체가 제공됩니다. 이 들어오는 데이터 개체는 일반적으로 EE에 의해 구현되지 않습니다. 그러나 이 메서드에서 반환되는 개체는 항상 EE에 의해 구현되어 `IEEDataStorage` EE가 원하는 클래스에 대한 인터페이스를 구현할 수 있습니다.

 들어오는 `IEEDataStorage` 개체에서 제공하는 데이터는 나가는 `IEEDataStorage` 개체의 동일한 데이터여야 합니다.

## <a name="see-also"></a>참조
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)

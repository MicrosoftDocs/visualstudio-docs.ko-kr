---
title: 'IPropertyProxyEESide:: CreateReplacementObject | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715044"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
식 계산기 (EE)와 관련 된 데이터 개체의 복사본을 만듭니다.

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
진행 복사할 데이터를 보유 하는 [Ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) 개체입니다.

`dataOut`\
제한이 새 개체를 반환 `IEEDataStorage` 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드에는 바이트 배열을 나타내는 [Ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) 개체가 제공 됩니다. 이 들어오는 데이터 개체는 일반적으로 EE에서 구현 하지 않습니다. 그러나이 메서드에서 반환 하는 개체는 항상 EE에서 구현 되므로 EE에서 `IEEDataStorage` 원하는 클래스에 대해 인터페이스를 구현할 수 있습니다.

 들어오는 개체가 제공 하는 데이터는 `IEEDataStorage` 나가는 개체의 데이터와 같아야 합니다 `IEEDataStorage` .

## <a name="see-also"></a>추가 정보
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)

---
title: IPropertyProxyEESide::InitSourceDataProvider | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f14f24836beb1d69a15149a56a2817ebf14eff55
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714906"
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
이 개체의 원본 데이터를 초기화하고 초기 데이터가 포함된 개체를 반환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT InitSourceDataProvider(
   IEEDataStorage** dataOut
);
```

```csharp
int InitSourceDataProvider(
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>매개 변수
`dataOut`\
【아웃】 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 개체 반환

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드는 개체의 데이터에 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 인터페이스를 반환할 수 있도록 개체를 초기화하는 데 필요한 모든 작업을 수행합니다. 이렇게 하면 개체의 데이터를 볼 수 있으며, 허용되는 경우 형식 시각화 도우미에 의해 변경될 수 있습니다.

## <a name="see-also"></a>참조
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)

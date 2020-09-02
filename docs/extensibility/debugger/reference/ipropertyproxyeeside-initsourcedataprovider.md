---
title: 'IPropertyProxyEESide:: InitSourceDataProvider | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714906"
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
이 개체의 원본 데이터를 초기화 하 고 초기 데이터를 포함 하는 개체를 반환 합니다.

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
제한이 [Ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 개체의 데이터에 대해 [Ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) 인터페이스를 반환할 수 있도록 개체를 초기화 하는 데 필요한 모든 항목을 수행 합니다. 이를 통해 개체의 데이터를 볼 수 있으며, 허용 된 경우 형식 시각화 도우미에 의해 변경 될 수 있습니다.

## <a name="see-also"></a>추가 정보
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)

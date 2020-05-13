---
title: IEE데이터 스토리지::겟데이터 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62a1295aeb2a6afad51dee0f1015e3ab01d13fbb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718216"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
개체에서 지정된 바이트 수를 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetData(
   ULONG  dataSize,
   ULONG* sizeGotten,
   BYTE*  data
);
```

```csharp
int GetData(
   uint     dataSize,
   out uint sizeGotten,
   byte[]   data
);
```

## <a name="parameters"></a>매개 변수
`dataSize`\
【인】 검색할 바이트 수입니다(배열은 `data` 최소한 이 바이트 수를 보유해야 합니다).

`sizeGotten`\
【아웃】 실제로 검색된 바이트 수를 반환합니다.

`data`\
【인, 아웃】 요청된 데이터로 채울 배열입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드의 권장된 용도는 검색 프로세스에서 바이트를 건너뛸 수 있는 방법이 없으므로 로컬 배열로 모든 데이터 바이트를 검색하는 것입니다. 이 경우 매개 `dataSize` 변수는 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) 메서드에서 반환 되는 값 이어야 합니다.

## <a name="see-also"></a>참조
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)

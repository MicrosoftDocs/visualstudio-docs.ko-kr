---
description: 개체에서 지정 된 바이트 수를 검색 합니다.
title: 'IEEDataStorage:: GetData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 218ffea2d35f34768550938e8bdc4c087bb3a2cf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083546"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
개체에서 지정 된 바이트 수를 검색 합니다.

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
진행 검색할 바이트 수 `data` 입니다 (배열에 최소한이 바이트 수를 포함 해야 함).

`sizeGotten`\
제한이 실제로 검색 된 바이트 수를 반환 합니다.

`data`\
[in, out] 요청한 데이터로 채워질 배열입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 검색 프로세스에서 바이트를 건너뛸 방법이 없으므로이 메서드를 사용 하는 것이 가장 좋습니다. 모든 데이터 바이트를 로컬 배열로 검색 하는 것입니다. 이 경우 매개 변수는 `dataSize` [getsize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) 메서드에서 반환 되는 값 이어야 합니다.

## <a name="see-also"></a>참조
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)

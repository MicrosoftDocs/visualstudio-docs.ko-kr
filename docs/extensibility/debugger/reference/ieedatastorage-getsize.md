---
title: IEEDataStorage::겟사이즈 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e7d9000889d082826f46bdceb0476dd5d06c24d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718202"
---
# <a name="ieedatastoragegetsize"></a>IEEDataStorage::GetSize
이 개체에 포함된 바이트 수를 반환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetSize(
   ULONG* size
);
```

```csharp
int GetSize(
   out uint size
);
```

## <a name="parameters"></a>매개 변수
`size`\
【아웃】 이 개체에 포함된 바이트 수입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) 메서드를 사용하여 실제 데이터 바이트를 검색합니다.

## <a name="see-also"></a>참조
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)

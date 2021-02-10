---
title: 'IEEDataStorage:: GetSize | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2a18ae08500bd457f6e9ab316514836a30538a42
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965514"
---
# <a name="ieedatastoragegetsize"></a>IEEDataStorage::GetSize
이 개체에 포함 된 바이트 수를 반환 합니다.

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
제한이 이 개체에 포함 된 바이트 수입니다.

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) 메서드를 사용 하 여 실제 데이터 바이트를 검색 합니다.

## <a name="see-also"></a>참고 항목
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)

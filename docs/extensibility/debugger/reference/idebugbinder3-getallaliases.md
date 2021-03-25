---
description: 이 메서드는 프로그램에서 별칭 목록을 검색 합니다.
title: 'IDebugBinder3:: GetAllAliases | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04e4f9887ff8cfa68ad4fd4b09d160e3ec2d1eaf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085171"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
이 메서드는 프로그램에서 별칭 목록을 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetAllAliases(
   UINT          uRequest,
   IDebugAlias** ppAliases,
   UINT*         puFetched
);
```

```csharp
int GetAllAliases(
   uint          uRequest,
   IDebugAlias[] ppAliases,
   out uint      puFetched
);
```

## <a name="parameters"></a>매개 변수
`uRequest`\
진행 반환할 별칭의 최대 수입니다 (로 전달 되는 배열의 길이를 지정 `ppAliases` ).

`ppAliases`\
[in, out] 별칭으로 채울 배열입니다 .이 값이 null 값이 고 `uRequest` 가 0 이면에서 반환 될 수 있는 별칭 수가 반환 됩니다 `puFetched` .

`puFetched`\
제한이 가져온 별칭의 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참조
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)

---
title: 이데버그바인더3:겟알리아스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2d512fa6eb7529e11c766d7c173b318aa6f8f2f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735814"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
이 메서드는 프로그램에서 별칭 목록을 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetAllAliases(
   UINT          uRequest,
   IDebugAlias** ppAliases,
   UINT*         puFetched
);
```

```csharp
int GetAllAliases(
   uint          uRequest,
   IDebugAlias[] ppAliases,
   out uint      puFetched
);
```

## <a name="parameters"></a>매개 변수
`uRequest`\
【인】 반환할 별칭의 최대 수(전달된 배열의 길이를 `ppAliases`지정함).

`ppAliases`\
【인, 아웃】 별칭으로 채울 배열(null 값이고 `uRequest` 0인 경우 반환할 수 있는 별칭 수가 `puFetched`반환됨).

`puFetched`\
【아웃】 가져온 별칭 수를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)

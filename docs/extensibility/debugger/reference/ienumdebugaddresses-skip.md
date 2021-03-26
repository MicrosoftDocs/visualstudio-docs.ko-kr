---
description: 이 메서드는 addresses 열거에서 지정 된 수의 요소를 건너뜁니다.
title: 'IEnumDebugAddresses:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Skip
helpviewer_keywords:
- IEnumDebugAddresses::Skip method
ms.assetid: ed9a8e71-30ef-414b-9da5-c9a2a251b84e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 082cba541b1074e75e44384cd8ac9e4879cc29c3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083156"
---
# <a name="ienumdebugaddressesskip"></a>IEnumDebugAddresses::Skip
이 메서드는 지정 된 수의 요소를 건너뜁니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Skip(
   [in] ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

## <a name="parameters"></a>매개 변수
`celt`\
진행 건너뛸 요소 수입니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. `S_FALSE` `celt` 가 나머지 요소 수보다 크면를 반환 하 고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 가 `celt` 나머지 요소 수보다 큰 값을 지정 하는 경우 열거형은 end로 설정 되 고 `S_FALSE` 이 반환 됩니다.

## <a name="see-also"></a>참조
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)

---
title: 아이디버그필드::평등 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8a45a31c02376f95c3cd6b0c4a4adf0434fabe92
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729017"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
이 메서드는 이 필드를 같음의 지정된 필드와 비교합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Equal( 
   IDebugField* pField
);
```

```csharp
int Equal(
   IDebugField pField
);
```

## <a name="parameters"></a>매개 변수
`pField`\
【인】 이 필드와 비교할 수 있습니다.

## <a name="return-value"></a>Return Value
 필드가 동일한 경우 을 `S_OK`반환합니다. 필드가 다른 경우 `S_FALSE.` 그렇지 않으면 반환하고 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

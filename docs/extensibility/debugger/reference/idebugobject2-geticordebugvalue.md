---
title: 아이디버그오브젝트2::겟디코르데버그 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetICorDebugValue
helpviewer_keywords:
- IDebugObject2::GetICorDebugValue method
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d52701b916650bc142038ffd96dcab8b05ec6da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726123"
---
# <a name="idebugobject2geticordebugvalue"></a>IDebugObject2::GetICorDebugValue
이 개체와 연결된 값을 나타내는 관리 되는 코드 개체를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>매개 변수
`ppUnk`\
【아웃】 `IUnknown` 이 별칭을 나타내는 인터페이스입니다. 이 인터페이스는 인터페이스에 `ICorDebugValue` 대해 쿼리할 수 있습니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 개체는 `ICorDebugValue` 값을 나타내는 공통 언어 런타임 인터페이스입니다.

## <a name="see-also"></a>참조
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)

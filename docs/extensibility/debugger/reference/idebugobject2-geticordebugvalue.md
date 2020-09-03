---
title: 'IDebugObject2:: GetICorDebugValue | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726123"
---
# <a name="idebugobject2geticordebugvalue"></a>IDebugObject2::GetICorDebugValue
이 개체와 연결 된 값을 나타내는 관리 되는 코드 개체를 가져옵니다.

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
[out] `IUnknown` 이 별칭을 나타내는 인터페이스입니다. 인터페이스에 대해이 인터페이스를 쿼리할 수 있습니다 `ICorDebugValue` .

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 `ICorDebugValue`개체는 값을 나타내는 공용 언어 런타임 인터페이스입니다.

## <a name="see-also"></a>추가 정보
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)

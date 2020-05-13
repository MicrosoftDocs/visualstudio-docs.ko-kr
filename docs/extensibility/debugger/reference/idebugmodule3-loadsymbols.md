---
title: IDebugModule3::로드 심볼 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c61339305200acc9a6c572a1a96595dc4cb6f50
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726782"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
현재 모듈의 기호를 로드합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT LoadSymbols(
   void
);
```

```csharp
int LoadSymbols();
```

## <a name="return-value"></a>Return Value
 메서드가 성공하면 `S_OK`가 반환되고, 그렇지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 이 메서드는 현재 검색 경로에서 기호를 [로드합니다(SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) 메서드를 호출하여 변경할 수 있음).

 이 방법은 [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) 방법보다 선호됩니다.

## <a name="see-also"></a>참조
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)

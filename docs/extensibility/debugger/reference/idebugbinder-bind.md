---
title: 이데버그바인더::바인드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7a783025c96053a89956a1c77d46b5e417938a2b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736024"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
이 메서드는 기호의 현재 값을 포함 하는 메모리 컨텍스트 또는 개체를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Bind( 
   IDebugObject*  pContainer,
   IDebugField*   pField,
   IDebugObject** ppObject
);
```

```csharp
int Bind(
   IDebugObject     pContainer,
   IDebugField      pField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>매개 변수
`pContainer`\
【인】 에서 참조하는 자식이 포함된 `pField` [IDebugObject입니다.](../../../extensibility/debugger/reference/idebugobject.md)

`pField`\
【인】 기호를 나타내는 [IDebugField입니다.](../../../extensibility/debugger/reference/idebugfield.md)

`ppObject`\
【아웃】 기호의 `IDebugObject` 인스턴스를 나타내는 것을 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

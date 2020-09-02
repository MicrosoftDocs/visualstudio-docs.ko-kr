---
title: 'IDebugBinder:: Bind | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
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
진행 에서 참조 하는 자식을 포함 하는 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 입니다 `pField` .

`pField`\
진행 기호를 나타내는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 입니다.

`ppObject`\
제한이 `IDebugObject` 기호의 인스턴스를 나타내는을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>추가 정보
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

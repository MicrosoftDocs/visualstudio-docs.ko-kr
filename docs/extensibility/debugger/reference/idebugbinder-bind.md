---
description: 이 메서드는 기호의 현재 값을 포함 하는 메모리 컨텍스트 또는 개체를 가져옵니다.
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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c373fbdae030de30544c67c1509eb812b746b7f1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143661"
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

## <a name="see-also"></a>참고 항목
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

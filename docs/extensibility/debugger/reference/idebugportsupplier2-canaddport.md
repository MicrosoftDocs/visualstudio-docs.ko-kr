---
title: IDebugPort Supplier2::CanAddPort | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5d0c67d62f57076f29f2c2ef60d456f517ae97fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724753"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
포트 공급자가 새 포트를 추가할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CanAddPort( 
   void 
);
```

```csharp
int CanAddPort();
```

## <a name="return-value"></a>Return Value
 포트를 추가할 수 있는 `S_OK`경우 반환합니다. 그렇지 않으면 `S_FALSE` 이 포트 공급자에 포트를 추가할 수 없음을 나타내는 반환입니다.

## <a name="remarks"></a>설명
 후자의 메서드는 포트를 만들고 추가할 뿐만 아니라 시간이 많이 소요될 수 있으므로 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 메서드를 호출하기 전에 이 메서드를 호출합니다.

## <a name="see-also"></a>참조
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)

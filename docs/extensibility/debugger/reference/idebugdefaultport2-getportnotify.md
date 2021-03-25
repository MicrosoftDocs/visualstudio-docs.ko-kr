---
description: 이 메서드는이 포트에 대 한 IDebugPortNotify2 인터페이스를 가져옵니다.
title: 'IDebugDefaultPort2:: GetPortNotify | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8ed43d96a7035dbd9e75a8e64a23e556997e087c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077475"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
이 메서드는이 포트에 대 한 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) 인터페이스를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetPortNotify(
   IDebugPortNotify2** ppPortNotify
);
```

```csharp
int GetPortNotify(
   out IDebugPortNotify2 ppPortNotify
);
```

## <a name="parameters"></a>매개 변수
`ppPortNotify`\
제한이 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 일반적으로 `QueryInterface` [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 인터페이스를 구현 하는 개체에서 메서드를 호출 하 여 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) 인터페이스를 가져옵니다. 그러나 원하는 인터페이스가 다른 개체에서 구현 되는 경우도 있습니다. 이 메서드는 이러한 상황을 숨기고 `IDebugPortNotify2` 가장 적절 한 개체에서 인터페이스를 반환 합니다.

## <a name="see-also"></a>참조
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)

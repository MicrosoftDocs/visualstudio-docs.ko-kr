---
title: IDebugDefaultPort2::GetServer | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetServer
helpviewer_keywords:
- IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3dbe6d813b85865b0fdbc20296473684203a3f1e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732377"
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
이 메서드는 이 포트가 있는 서버에 대한 인터페이스를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetServer(
   IDebugCoreServer3** ppServer
);
```

```csharp
int GetServer(
   out IDebugCoreServer3 ppServer
);
```

## <a name="parameters"></a>매개 변수
`ppServer`\
【아웃】 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) 인터페이스를 구현하는 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 [IDebugCoreServer3는](../../../extensibility/debugger/reference/idebugcoreserver3.md) Visual Studio에서 구현되며 포트가 있는 서버를 나타냅니다.

## <a name="see-also"></a>참조
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)

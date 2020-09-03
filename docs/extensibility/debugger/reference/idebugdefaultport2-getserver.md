---
title: 'IDebugDefaultPort2:: GetServer | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732377"
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
이 메서드는이 포트가 있는 서버에 대 한 인터페이스를 가져옵니다.

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
제한이 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) 인터페이스를 구현 하는 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) 는 Visual Studio에서 구현 되며 포트가 있는 서버를 나타냅니다.

## <a name="see-also"></a>추가 정보
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)

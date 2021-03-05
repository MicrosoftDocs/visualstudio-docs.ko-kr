---
description: 포트를 만든 데 이전에 사용 된 포트에 대 한 설명을 가져옵니다 (있는 경우).
title: 'IDebugPort2:: GetPortRequest | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 084e8bb94356ea4e2cff1fa83e83e7e08b35134e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142871"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
포트를 만든 데 이전에 사용 된 포트에 대 한 설명을 가져옵니다 (있는 경우).

## <a name="syntax"></a>구문

```cpp
HRESULT GetPortRequest( 
   IDebugPortRequest2** ppRequest
);
```

```csharp
int GetPortRequest( 
   out IDebugPortRequest2 ppRequest
);
```

## <a name="parameters"></a>매개 변수
`ppRequest`\
제한이 포트를 만드는 데 사용 된 요청을 나타내는 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  `E_PORT_NO_REQUEST` [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) port 요청을 사용 하 여 포트를 만들지 않은 경우를 반환 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)

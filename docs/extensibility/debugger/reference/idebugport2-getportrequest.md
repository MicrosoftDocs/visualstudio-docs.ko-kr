---
title: 아이디버그포트2:겟포트요청 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d48d39ea10e8425d5449444514489ac4b73c0a3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725340"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
포트를 만드는 데 이전에 사용되었던 포트에 대한 설명을 가져옵니다(사용 가능한 경우).

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
【아웃】 포트를 만드는 데 사용된 요청을 나타내는 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.  `E_PORT_NO_REQUEST` [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) 포트 요청을 사용하여 포트를 만들지 않은 경우 반환합니다.

## <a name="see-also"></a>참조
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)

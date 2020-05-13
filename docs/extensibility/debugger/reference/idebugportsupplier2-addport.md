---
title: 아이디버그포트공급업체2:애드포트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 00954ceaa0ddd750a3d08e372d1edaa1905f01c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724733"
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
포트를 추가합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT AddPort( 
   IDebugPortRequest2* pRequest,
   IDebugPort2**       ppPort
);
```

```csharp
int AddPort( 
   IDebugPortRequest2 pRequest,
   out IDebugPort2    ppPort
);
```

## <a name="parameters"></a>매개 변수
`pRequest`\
【인】 추가할 포트를 설명하는 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) 개체입니다.

`ppPort`\
【아웃】 포트를 나타내는 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드는 실제로 요청된 포트를 만들고 포트 공급자의 활성 포트 의 내부 목록에 추가 합니다. [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) 메서드를 먼저 호출하여 시간이 오래 걸리는 지연을 방지할 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)

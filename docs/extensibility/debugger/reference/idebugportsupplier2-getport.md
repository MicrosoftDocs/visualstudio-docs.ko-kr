---
title: 아이디버그포트공급업체2:겟포트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::GetPort
helpviewer_keywords:
- IDebugPortSupplier2::GetPort
ms.assetid: d55d5055-7386-4037-bf22-4c3e434a99ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be3f53c12b5562377cd79267d6e216a1435859a5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724659"
---
# <a name="idebugportsupplier2getport"></a>IDebugPortSupplier2::GetPort
포트 공급자로부터 포트를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetPort( 
   REFGUID       guidPort,
   IDebugPort2** ppPort
);
```

```csharp
int GetPort( 
   ref Guid        guidPort,
   out IDebugPort2 ppPort
);
```

## <a name="parameters"></a>매개 변수
`guidPort`\
【인】 포트의 전역 고유 식별자(GUID)입니다.

`ppPort`\
【아웃】 포트를 나타내는 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 지정된 `E_PORTSUPPLIER_NO_PORT` 식별자가 있는 포트가 없는 경우 반환합니다.

## <a name="see-also"></a>참조
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)

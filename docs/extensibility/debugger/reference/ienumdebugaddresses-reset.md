---
title: IEnumDebug 주소::재설정 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Reset
helpviewer_keywords:
- IEnumDebugAddresses::Reset method
ms.assetid: 3a9d7f20-5bc6-4e13-8e91-5af4092e092f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 48026ee5f359c80c2c807fa857f1ec749823e2b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717629"
---
# <a name="ienumdebugaddressesreset"></a>IEnumDebugAddresses::Reset
이 메서드는 열거형에서 첫 번째 요소로 다시 설정합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

## <a name="parameters"></a>매개 변수
 None

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드가 호출된 후 [Next에](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md) 대한 다음 호출은 열거형의 첫 번째 요소를 반환합니다.

## <a name="see-also"></a>참조
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
- [다음](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)

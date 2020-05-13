---
title: IDebugProcess3:GetENC사용 가능 상태 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetENCAvailableState
helpviewer_keywords:
- IDebugProcess3::GetENCAvailableState
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77345cfc3aa1dd95482052893e7c09591ad7cd4e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723649"
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
이 메서드는 프로세스의 현재 편집 및 계속 상태를 가져옵니다. 사용자 지정 포트 공급자는 항상 반환해야 `E_NOTIMPL`합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetENCAvailableState(
   EncUnavailableReason* pReason
);
```

```csharp
int GetENCAvailableState(
   EncUnavailableReason[] pReason
);
```

## <a name="parameters"></a>매개 변수
`pReason`\
【아웃】 [EncUnavailable에서 값이유](../../../extensibility/debugger/reference/encunavailablereason.md) 열거.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

> [!NOTE]
> 사용자 지정 포트 공급자는 항상 반환해야 `E_NOTIMPL`합니다.

## <a name="remarks"></a>설명
 이 상태는 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)의 영향을 받을 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)

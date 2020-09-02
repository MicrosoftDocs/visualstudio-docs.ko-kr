---
title: 'IDebugProcess3:: Getenc 상태 | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723649"
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
이 메서드는 프로세스의 현재 편집 하며 계속 하기 상태를 가져옵니다. 사용자 지정 포트 공급자는 항상를 반환 해야 합니다 `E_NOTIMPL` .

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
제한이 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) 열거형의 값입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

> [!NOTE]
> 사용자 지정 포트 공급자는 항상를 반환 해야 합니다 `E_NOTIMPL` .

## <a name="remarks"></a>설명
 이 상태는 [Disableenc](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)의 영향을 받을 수 있습니다.

## <a name="see-also"></a>추가 정보
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)

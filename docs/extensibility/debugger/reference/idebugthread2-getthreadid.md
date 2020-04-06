---
title: IDebugThread2::GetThreadId | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetThreadId
helpviewer_keywords:
- IDebugThread2::GetThreadId
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a7788cc09d92ff4c784fbcb7004393fe0d3074c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718711"
---
# <a name="idebugthread2getthreadid"></a>IDebugThread2::GetThreadId
시스템 스레드 식별자를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetThreadId (
    DWORD* pdwThreadId
);
```

```csharp
int GetThreadId (
    out uint pdwThreadId
);
```

## <a name="parameters"></a>매개 변수
`pdwThreadId`\
【아웃】 시스템 스레드 식별자를 반환합니다.

## <a name="return-value"></a>Return Value
성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
스레드 ID는 프로세스의 다른 모든 스레드 간에 스레드를 식별하는 데 사용됩니다.

## <a name="example"></a>예제
다음 예제에서는 `CProgram` [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 인터페이스를 구현 하는 간단한 개체에 대 한이 메서드를 구현 하는 방법을 보여 줍니다.

```cpp
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {
    *pdwThreadId = GetCurrentThreadId();
    return NOERROR;
}
```

## <a name="see-also"></a>참조
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)

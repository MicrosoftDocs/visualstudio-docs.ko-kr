---
description: 시스템 스레드 식별자를 가져옵니다.
title: 'IDebugThread2:: GetThreadId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetThreadId
helpviewer_keywords:
- IDebugThread2::GetThreadId
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 39702dad7ad154e2922f217f36c13a47588cb06d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053037"
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
제한이 시스템 스레드 식별자를 반환 합니다.

## <a name="return-value"></a>반환 값
성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
스레드 ID는 프로세스의 다른 모든 스레드 간에 스레드를 식별 하는 데 사용 됩니다.

## <a name="example"></a>예제
다음 예제에서는 IDebugThread2 인터페이스를 구현 하는 간단한 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다 `CProgram` . [](../../../extensibility/debugger/reference/idebugthread2.md)

```cpp
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {
    *pdwThreadId = GetCurrentThreadId();
    return NOERROR;
}
```

## <a name="see-also"></a>참조
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)

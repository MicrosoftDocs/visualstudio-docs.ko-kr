---
title: IDebug예외2::캔패스토디버그지 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab57f599214cfbd7a1f5fcca15fa104b072d1d48
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729875"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
DE(디버그 엔진)가 실행이 다시 시작될 때 디버깅되는 프로그램에 이 예외를 전달하는 옵션을 지원하는지 여부를 결정합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>Return Value
 반환 `S_OK` 중 하나 (예외는 프로그램에 전달 `S_FALSE` 될 수 있습니다) 또는 (예외는 전달 될 수 없습니다).

## <a name="remarks"></a>설명
 DE에는 디버그지에 전달하기 위한 기본 작업이 있어야 합니다. IDE는 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) 이벤트를 수신하고 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) 메서드를 호출하지 `CanPassToDebuggee` 않고 Continue 메서드를 호출할 수 있습니다. 따라서 DE에는 예외를 전달하거나 하지 않는 기본 사례가 있어야 합니다.

## <a name="see-also"></a>참조
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [계속](../../../extensibility/debugger/reference/idebugprocess3-continue.md)

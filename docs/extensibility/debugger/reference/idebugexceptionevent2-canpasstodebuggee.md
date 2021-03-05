---
description: 디버그 엔진 (DE)이 실행을 다시 시작할 때 디버깅 중인 프로그램에이 예외를 전달 하는 옵션을 지원 하는지 여부를 결정 합니다.
title: 'IDebugExceptionEvent2:: Can Sto디버기 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b56996a5fa7cbf3c08842b783aa2d5dfc1131b8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152886"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
디버그 엔진 (DE)이 실행을 다시 시작할 때 디버깅 중인 프로그램에이 예외를 전달 하는 옵션을 지원 하는지 여부를 결정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>Return Value
 는 `S_OK` (예외를 프로그램에 전달할 수 있음) 또는 `S_FALSE` (예외를 전달할 수 없음)을 반환 합니다.

## <a name="remarks"></a>설명
 DE에는 디버기에 전달 하기 위한 기본 작업이 있어야 합니다. IDE는 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) 이벤트를 수신 하 고 메서드를 호출 하지 않고 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) 메서드를 호출할 수 있습니다 `CanPassToDebuggee` . 따라서 DE에는 예외를 전달 하기 위한 기본 사례가 있어야 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [계속](../../../extensibility/debugger/reference/idebugprocess3-continue.md)

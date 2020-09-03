---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab57f599214cfbd7a1f5fcca15fa104b072d1d48
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729875"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
디버그 엔진 (DE)이 실행을 다시 시작할 때 디버깅 중인 프로그램에이 예외를 전달 하는 옵션을 지원 하는지 여부를 결정 합니다.

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
 는 `S_OK` (예외를 프로그램에 전달할 수 있음) 또는 `S_FALSE` (예외를 전달할 수 없음)을 반환 합니다.

## <a name="remarks"></a>설명
 DE에는 디버기에 전달 하기 위한 기본 작업이 있어야 합니다. IDE는 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) 이벤트를 수신 하 고 메서드를 호출 하지 않고 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) 메서드를 호출할 수 있습니다 `CanPassToDebuggee` . 따라서 DE에는 예외를 전달 하기 위한 기본 사례가 있어야 합니다.

## <a name="see-also"></a>추가 정보
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [계속](../../../extensibility/debugger/reference/idebugprocess3-continue.md)

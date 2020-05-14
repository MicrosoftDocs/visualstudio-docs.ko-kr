---
title: IDebugStackFrame3::절편현재예외 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7debd5323e753c6c5fd1476eac3c062fb63393b9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719485"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
현재 예외를 가로채려는 경우 현재 스택 프레임의 디버거에서 호출합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT InterceptCurrentException(
   INTERCEPT_EXCEPTION_ACTION dwFlags,
   UINT64*                    pqwCookie
);
```

```csharp
int InterceptCurrentException(
   uint dwFlags,
   out  ulong pqwCookie
);
```

## <a name="parameters"></a>매개 변수
`dwFlags`\
【인】 다른 작업을 지정합니다. 현재는 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) 값만 `IEA_INTERCEPT` 지원되며 지정해야 합니다.

`pqwCookie`\
【아웃】 특정 예외를 식별하는 고유 값입니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

 다음은 가장 일반적인 오류 반환입니다.

|Error|설명|
|-----------|-----------------|
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|현재 예외는 가로챌 수 없습니다.|
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|현재 실행 프레임은 아직 처리기를 검색하지 않았습니다.|
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|이 메서드는 이 프레임에 대해 지원되지 않습니다.|

## <a name="remarks"></a>설명
 예외가 throw되면 디버거는 예외 처리 프로세스 중에 키 포인트에서 런타임으로부터 제어를 얻습니다. 이러한 중요한 순간에 디버거는 프레임이 예외를 가로채려는 경우 현재 스택 프레임을 요청할 수 있습니다. 이러한 방식으로 가로채진 예외는 스택 프레임에 대한 온-더-플라이(on-the-fly) 예외 처리기(예: 프로그램 코드의 try/catch 블록)가 없는 경우에도 기본적으로 스택 프레임에 대한 즉석 예외 처리기입니다.

 디버거가 예외를 가로챌지 알고 자할 때 현재 스택 프레임 개체에서 이 메서드를 호출합니다. 이 메서드는 예외의 모든 세부 정보를 처리 합니다. [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) 인터페이스가 구현되지 않았거나 `InterceptStackException` 메서드가 오류를 반환하면 디버거가 예외를 정상적으로 처리합니다.

> [!NOTE]
> 예외는 관리 코드에서만 가로챌 수 있습니다. 물론 타사 언어 구현자는 원하는 `InterceptStackException` 경우 자체 디버그 엔진에서 구현할 수 있습니다.

 가로채기가 완료되면 [IDebugIntercept예외불완전이벤트2가](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) 신호를 보신다.

## <a name="see-also"></a>참조
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)

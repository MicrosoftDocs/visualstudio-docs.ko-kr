---
title: IDebugStackFrame3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d86997d11e124fd5a47981314cf383f5cd8aff7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719476"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
이 인터페이스는 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 를 확장 하 여 차단 되는 예외를 처리 합니다.

## <a name="syntax"></a>Syntax

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE (디버그 엔진)는 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 인터페이스를 구현 하는 동일한 개체에서이 인터페이스를 구현 하 여 가로채는 예외를 지원 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 인터페이스에서 [QueryInterface](/cpp/atl/queryinterface) `IDebugStackFrame2` 를 호출 하 여이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)에서 상속 된 메서드 외에도 `IDebugStackFrame3` 는 다음 메서드를 노출 합니다.

|메서드|설명|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|일반적인 예외 처리 전에 현재 스택 프레임에 대 한 예외를 처리 합니다.|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|스택 해제가 발생 하는 경우 코드 컨텍스트를 반환 합니다.|

## <a name="remarks"></a>설명
 가로채기 예외는 디버거가 일반적인 예외 처리 루틴을 호출 하기 전에 예외를 처리할 수 있음을 의미 합니다. 예외를 가로채는 것은 기본적으로 실행 시간을 사용 하면 예외 처리기가 없는 경우에도 표시 됩니다.

- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) 는 모든 일반 예외 콜백 이벤트 중에 호출 됩니다 .이 경우에는 혼합 모드 코드 (관리 코드 및 비관리 코드)를 디버깅 하는 경우에만 예외가 발생 합니다 .이 경우에는 마지막 콜백을 수행 하는 동안 예외를 가로챌 수 없습니다. DE가을 구현 하지 `IDebugStackFrame3` 않거나 de가 IDebugStackFrame3:: (예:)에서 오류를 반환 하는 경우 `InterceptCurrentException` `E_NOTIMPL` 디버거는이 예외를 정상적으로 처리 합니다.

 예외를 가로채 면 디버거를 사용 하 여 디버깅 중인 프로그램의 상태를 변경 하 고 예외가 throw 된 지점에서 실행을 다시 시작할 수 있습니다.

> [!NOTE]
> 예외 가로채기는 관리 코드, 즉 CLR (공용 언어 런타임)에서 실행 되는 프로그램 에서만 사용할 수 있습니다.

 디버그 엔진은 함수를 사용 하 여 런타임 시 "metricExceptions"을 값 1로 설정 하 여 예외 가로채기를 지원함을 나타냅니다 `SetMetric` . 자세한 내용은 [디버깅을 위한 SDK 도우미](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [디버깅을 위한 SDK 도우미](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

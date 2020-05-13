---
title: 아이디버그스택프레임3 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719476"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
이 인터페이스는 차단된 예외를 처리하기 위해 [IDebugStackFrame2를](../../../extensibility/debugger/reference/idebugstackframe2.md) 확장합니다.

## <a name="syntax"></a>구문

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진(DE)은 차단된 예외를 지원하기 위해 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 인터페이스를 구현하는 동일한 개체에 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스를 `IDebugStackFrame2` 얻으려면 인터페이스에서 [QueryInterface를](/cpp/atl/queryinterface) 호출합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 [IDebugStackFrame2에서](../../../extensibility/debugger/reference/idebugstackframe2.md)상속된 메서드 외에도 `IDebugStackFrame3` 다음 메서드를 노출합니다.

|방법|설명|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|일반 예외 처리 전에 현재 스택 프레임에 대한 예외를 처리합니다.|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|스택 해제가 발생할 경우 코드 컨텍스트를 반환합니다.|

## <a name="remarks"></a>설명
 가로채기 된 예외는 실행 시간에 의해 정상적인 예외 처리 루틴이 호출되기 전에 디버거가 예외를 처리할 수 있음을 의미합니다. 예외를 가로채는 것은 기본적으로 런타임이 없는 경우에도 예외 처리기가 있는 것처럼 가장하는 것을 의미합니다.

- [InterceptCurrentException은](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) 모든 일반 예외 콜백 이벤트 중에 호출됩니다(이에 대한 유일한 예외는 혼합 모드 코드(관리 및 관리되지 않는 코드)를 디버깅하는 경우이며, 이 경우 마지막 기회 콜백 중에 예외를 가로챌 수 없습니다. DE가 구현하지 `IDebugStackFrame3`않거나 DE가 IDebugStackFrame3::`InterceptCurrentException` (예:) `E_NOTIMPL`오류를 반환하면 디버거가 예외를 정상적으로 처리합니다.

 예외를 가로채서 디버거는 사용자가 디버깅 중인 프로그램의 상태를 변경한 다음 예외가 throw된 지점에서 실행을 다시 시작할 수 있도록 허용할 수 있습니다.

> [!NOTE]
> 가로챈 예외는 CLR(공통 언어 런타임)에서 실행 중인 프로그램에서 관리 코드, 즉 관리 코드에서만 허용됩니다.

 디버그 엔진은 `SetMetric` 함수를 사용하여 런타임에 "metricExceptions"를 1의 값으로 설정하여 예외를 가로채는 것을 지원한다는 것을 나타냅니다. 자세한 내용은 [디버깅에 대한 SDK 도우미를](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)참조하십시오.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [디버깅을 위한 SDK 도우미](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

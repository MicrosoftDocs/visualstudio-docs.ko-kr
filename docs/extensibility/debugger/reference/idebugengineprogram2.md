---
description: 이 인터페이스는 다중 스레드 디버깅을 지원 합니다.
title: IDebugEngineProgram2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ea46ccad8f357cb868a445a8836280abf7c224e0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153380"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
이 인터페이스는 다중 스레드 디버깅을 지원 합니다.

## <a name="syntax"></a>Syntax

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진은 여러 스레드의 동시 디버깅을 지원 하기 위해이 인터페이스를 구현 합니다. 이 인터페이스는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스를 구현 하는 동일한 개체에서 구현 됩니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 인터페이스에서이 인터페이스를 가져오려면 [QueryInterface](/cpp/atl/queryinterface) 를 사용 `IDebugProgram2` 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugEngineProgram2` .

|메서드|설명|
|------------|-----------------|
|[중지](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|이 프로그램에서 실행 중인 모든 스레드를 중지 합니다.|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|지정 된 스레드에서 실행을 감시 하거나 실행에 대 한 감시를 중지 합니다.|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|프로그램이 중지 된 경우에도 지정 된 스레드에서 식 계산을 수행 하도록 허용 하거나 허용 하지 않습니다.|

## <a name="remarks"></a>설명
 Visual Studio는 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 이벤트에 대 한 응답으로이 인터페이스를 호출 하 고, 프로그램의 "스레드 확인에 대 한 조사식" 및 "스레드 계산에 대 한 조사식" 상태를 설정 합니다. [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) 은 프로그램을 중지할 때마다 호출 됩니다. 이 메서드는 프로그램에 모든 스레드를 종료할 수 있는 기회를 제공 합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

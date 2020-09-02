---
title: IDebugExpressionEvaluationCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 35e57e361b59e76e187617b5e528b219e8e47897
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729565"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
이 인터페이스는 비동기 식 계산이 완료 되 면 디버그 엔진 (DE)에서 세션 디버그 관리자 (SDM)로 보냅니다.

## <a name="syntax"></a>Syntax

```
IDebugExpressionEvaluationCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE는이 인터페이스를 구현 하 여 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)에 대 한 호출로 시작 된 식 계산의 완료를 보고 합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는이 인터페이스와 동일한 개체에서 구현 되어야 합니다. SDM은 [QueryInterface](/cpp/atl/queryinterface) 를 사용 하 여 `IDebugEvent2` 인터페이스에 액세스 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 DE는이 이벤트 개체를 만들어이 이벤트 개체를 전송 하 여 식 계산의 완료를 보고 합니다. 이벤트는 디버깅 중인 프로그램에 연결 될 때 SDM에서 제공 하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용 하 여 보냅니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugExpressionEvaluationCompleteEvent2` .

|메서드|설명|
|------------|-----------------|
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|원래 식을 가져옵니다.|
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|식 계산 결과를 가져옵니다.|

## <a name="remarks"></a>설명
 평가가 성공 했는지 여부에 관계 없이 DE는이 이벤트를 보내야 합니다.

 평가가 실패 한 경우 `DEBUG_PROPINFO_VALUE` `DEBUG_PROPINFO_ATTRIB` [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 에서 반환 하는 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조에 및 플래그가 설정 되지 않습니다. [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 개체는 해제에 의해 생성 되 고 평가에 실패 한 경우에는 이벤트에서 반환 됩니다 `IDebugExpressionEvaluationCompleteEvent2` .

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

---
title: 아이디버그표현평가완료2 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729565"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
이 인터페이스는 비동기 식 평가가 완료되면 DE(디버그 엔진)를 세션 디버그 관리자(SDM)로 전송합니다.

## <a name="syntax"></a>구문

```
IDebugExpressionEvaluationCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE는 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)에 대한 호출로 시작된 식 평가의 완료를 보고하기 위해 이 인터페이스를 구현합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는 이 인터페이스와 동일한 개체에서 구현되어야 합니다. SDM은 [쿼리인터페이스를](/cpp/atl/queryinterface) 사용하여 `IDebugEvent2` 인터페이스에 액세스합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 DE는 이 이벤트 개체를 만들고 보내 식 평가의 완료를 보고합니다. 이 이벤트는 디버깅되는 프로그램에 연결될 때 SDM에서 제공하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용하여 전송됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugExpressionEvaluationCompleteEvent2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|원래 식을 가져옵니다.|
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|식 평가 결과를 가져옵니다.|

## <a name="remarks"></a>설명
 DE는 평가가 성공했는지 여부에 관계없이 이 이벤트를 보내야 합니다.

 평가에 `DEBUG_PROPINFO_VALUE` 성공하지 못한 경우 `DEBUG_PROPINFO_ATTRIB` 및 플래그는 [GetPropertyInfo에서](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 반환하는 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조에서 설정되지 않습니다(IDebugProperty2 개체는 DE에 의해 생성되고 평가가 실패한 경우 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) `IDebugExpressionEvaluationCompleteEvent2` 이벤트에서 반환됨).

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

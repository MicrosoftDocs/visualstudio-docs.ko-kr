---
title: IDebug표현컨텍스트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 344ae287b3784ceca87fbbab09ad2b2e0a304205
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729632"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
이 인터페이스는 식 평가를 위한 컨텍스트를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DEBug 엔진(DE)은 식을 평가할 수 있는 컨텍스트를 나타내기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [GetExpressionContext에](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 대한 호출은 이 인터페이스를 반환합니다. 이 인터페이스는 디버깅 중인 프로그램이 일시 중지되고 스택 프레임을 사용할 수 있는 경우에만 액세스할 수 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugExpressionContext2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|평가 컨텍스트의 이름을 검색합니다.|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|평가를 위해 텍스트 기반 식을 구문 분석합니다.|

## <a name="remarks"></a>설명
 평가 컨텍스트는 식 평가를 수행하기 위한 범위로 생각할 수 있습니다.

 프로그램이 중지되면 세션 디버그 관리자(SDM)는 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)를 호출하여 DE에서 스택 프레임을 가져옵니다. 그런 다음 SDM은 [GetExpressionContext를](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 호출하여 인터페이스를 `IDebugExpressionContext2` 가져옵니다. 그 다음에는 평가할 구문 분석식을 나타내는 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) 인터페이스를 만들기 위해 [ParseText를](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 호출합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)

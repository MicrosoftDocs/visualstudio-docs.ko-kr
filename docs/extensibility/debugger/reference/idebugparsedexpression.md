---
title: 아이데버그파르스표현 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22069b8eedb06d67eafaf7333f379a057c1b6f23
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726002"
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 평가기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 평가기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 이 인터페이스는 평가할 준비가 된 구문 분석식을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugParsedExpression : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 식 평가기는 이 인터페이스를 구현하여 평가할 준비가 된 구문 분석식을 나타냅니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [구문 분석에](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 대한 호출은 이 인터페이스를 반환합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugParsedExpression`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|구문 분석된 식을 평가합니다.|

## <a name="remarks"></a>설명
 호출자는 식을 평가할 준비가 되면 [EvaluateSync를](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 호출하여 평가 결과를 포함하는 [IDebugProperty2를](../../../extensibility/debugger/reference/idebugproperty2.md) 반환합니다. 평가에 대한 이 두 부분으로 구성된 접근 방식은 구문 분석 후 평가할 때 구문 분석식을 여러 번 평가할 수 있게 해 주며 표현식을 구문 분석하는 데 시간이 많이 걸리는 프로세스를 우회합니다.

## <a name="requirements"></a>요구 사항
 헤더: ee.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [구문 분석](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

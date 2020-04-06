---
title: 표현식 평가기 구현 전략 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3922689c20c839b3c0c2b2440bc9fefd5d25c80a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738678"
---
# <a name="expression-evaluator-implementation-strategy"></a>표현식 평가기 구현 전략
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 계산기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 식 계산기(EE)를 빠르게 만드는 한 가지 방법은 먼저 **Locals** 창에 지역 변수를 표시하는 데 필요한 최소 코드를 구현하는 것입니다. **Locals** 창의 각 줄에는 지역 변수의 이름, 형식 및 값이 표시되고 세 줄 모두 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 개체로 표시됩니다. 로컬 변수의 이름, 형식 및 값은 `IDebugProperty2` [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 메서드를 호출하여 개체에서 가져옵니다. 지역 변수를 **지역** 변수창에 표시하는 방법에 대한 자세한 내용은 [지역 변수 표시를](../../extensibility/debugger/displaying-locals.md)참조하십시오.

## <a name="discussion"></a>토론
 가능한 구현 순서는 [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)를 구현하는 것으로 시작됩니다. 지역 구시가지를 표시하려면 [구문 분석](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 및 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 메서드를 구현해야 합니다. 호출은 `IDebugExpressionEvaluator::GetMethodProperty` `IDebugProperty2` 메서드, 즉 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) 개체를 나타내는 개체를 반환합니다. 메서드 자체는 **지역 구시가지** 창에 표시되지 않습니다.

 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 메서드는 다음에 구현되어야 합니다. 디버그 엔진(DE)은 이 메서드를 호출하여 `IDebugProperty2::EnumChildren` `guidFilter` `guidFilterLocalsPlusArgs`의 인수를 전달하여 지역 변수 및 인수 목록을 가져옵니다. `IDebugProperty2::EnumChildren`단일 열거형에서 결과를 결합하여 열거형 및 [열거형 지역 주민을](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) [호출합니다.](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) 자세한 내용은 [지역 주민 표시를](../../extensibility/debugger/displaying-locals.md) 참조하십시오.

## <a name="see-also"></a>참조
- [식 계산기 구현](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [지역 주민 표시](../../extensibility/debugger/displaying-locals.md)

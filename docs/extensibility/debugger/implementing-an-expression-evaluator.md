---
title: 표현식 평가자 구현 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8c7c9a1130794dd4c28f212afd6cb3c030f5a1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738546"
---
# <a name="implement-an-expression-evaluator"></a>식 계산기 구현
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 계산기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 식을 평가하는 것은 디버그 엔진(DE), 심볼 공급자(SP), 바인더 오브젝트 및 식 평가기(EE) 간의 복잡한 상호 작용이다. 이러한 네 가지 구성 요소는 한 구성 요소에 의해 구현되고 다른 구성 요소에 의해 사용되는 인터페이스로 연결됩니다.

 EE는 DE에서 문자열 의 형태로 식을 가져와 구문 분석하거나 평가합니다. EE는 DE에서 사용하는 다음 인터페이스를 실행합니다.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  EE는 기호 및 개체의 값을 얻기 위해 DE에서 제공하는 바인더 개체를 호출합니다. EE는 DE에 의해 구현되는 다음 인터페이스를 사용합니다.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  EE는 [IDebugProperty2를](../../extensibility/debugger/reference/idebugproperty2.md)실행합니다. `IDebugProperty2`는 지역 변수, 기본 변수 또는 개체와 같은 식 평가 결과를 설명하는 메커니즘을 제공하며, 이 메커니즘은 **지역 변수,** **보기**또는 **즉시** 창에 적절한 정보를 표시합니다.

  SP는 정보를 요청할 때 DE에 의해 EE에 제공됩니다. SP는 다음 인터페이스 및 해당 파생 상품과 같은 주소 및 필드를 설명하는 인터페이스를 실행합니다.

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  EE는 이러한 모든 인터페이스를 사용합니다.

## <a name="in-this-section"></a>섹션 내용
 [표현식 평가기 구현 전략](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) 식 평가기(EE) 구현 전략에 대한 3단계 프로세스를 정의합니다.

## <a name="see-also"></a>참조
- [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

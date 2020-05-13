---
title: 키 표현식 평가기 인터페이스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01527edac4000f0b2f7b89fdd507fc093f0d7734
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738495"
---
# <a name="key-expression-evaluator-interfaces"></a>키 표현식 평가기 인터페이스
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 계산기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 식 평가기(EE)를 평가 컨텍스트와 함께 작성할 때는 다음 인터페이스에 대해 잘 알고 있어야 합니다.

## <a name="interface-descriptions"></a>인터페이스 설명

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     현재 실행 지점을 나타내는 데이터 구조를 얻는 단일 [메서드인 GetAddress가](../../extensibility/debugger/reference/idebugaddress-getaddress.md)있습니다. 이 데이터 구조는 디버그 엔진(DE)이 식을 평가하기 위해 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 메서드에 전달하는 세 가지 인수 중 하나입니다. 이 인터페이스는 일반적으로 기호 공급자에 의해 구현 됩니다.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     기호의 현재 값을 포함하는 메모리 영역을 가져오는 [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) 메서드가 있습니다. [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) 개체로 표시되는 포함 메서드와 [IDebugField](../../extensibility/debugger/reference/idebugfield.md) 개체로 표시되는 기호 자체가 모두 `IDebugBinder::Bind` 주어지면 기호의 값이 반환됩니다. `IDebugBinder`은 일반적으로 DE에 의해 구현됩니다.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     간단한 데이터 형식을 나타냅니다. 배열 및 메서드와 같은 보다 복잡한 형식의 경우 파생된 [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) 및 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) 인터페이스를 각각 사용합니다. [IDebugContainerField는](../../extensibility/debugger/reference/idebugcontainerfield.md) 메서드 또는 클래스와 같은 다른 기호를 포함하는 기호를 나타내는 또 다른 중요한 파생 인터페이스입니다. `IDebugField` 인터페이스(및 해당 파생 상품)는 일반적으로 심볼 공급자에 의해 구현됩니다.

     개체를 `IDebugField` 사용하여 기호의 이름과 형식을 찾을 수 있으며 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) 개체와 함께 해당 값을 찾을 수 있습니다.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     기호의 런타임 값의 실제 비트를 나타냅니다. [바인드는](../../extensibility/debugger/reference/idebugbinder-bind.md) 기호를 나타내는 [IDebugField](../../extensibility/debugger/reference/idebugfield.md) 개체를 가져와 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) 개체를 반환합니다. [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) 메서드는 메모리 버퍼에서 기호값을 반환합니다. DE는 일반적으로 메모리에 있는 속성의 값을 나타내기 위해 이 인터페이스를 구현합니다.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     이 인터페이스는 식 계산기 자체를 나타냅니다. 주요 방법은 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 인터페이스를 반환하는 [구문 분석입니다.](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     이 인터페이스는 평가할 준비가 된 구문 분석식을 나타냅니다. 키 메서드는 식의 값 과 형식을 나타내는 IDebugProperty2를 반환 하는 [EvaluateSync입니다.](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     이 인터페이스는 값과 해당 형식을 나타내며 식 평가의 결과입니다.

## <a name="see-also"></a>참조
- [평가 컨텍스트](../../extensibility/debugger/evaluation-context.md)

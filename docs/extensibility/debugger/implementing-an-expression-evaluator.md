---
title: 식 계산기 구현 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738546"
---
# <a name="implement-an-expression-evaluator"></a>식 계산기 구현
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.

 식 계산은 디버그 엔진 (DE), 기호 공급자 (SP), 바인더 개체 및 식 계산기 (EE) 사이에서 복잡 한 상호 작용입니다. 이러한 네 가지 구성 요소는 한 구성 요소에서 구현 되 고 다른 구성 요소에서 사용 하는 인터페이스에 의해 연결 됩니다.

 EE는 문자열 형식의 DE에서 식을 사용 하 고 구문 분석 하거나 계산 합니다. EE는 DE에서 사용 되는 다음 인터페이스를 실행 합니다.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  EE는 DE에서 제공 하는 바인더 개체를 호출 하 여 기호 및 개체의 값을 가져옵니다. EE는 DE에서 구현 하는 다음 인터페이스를 사용 합니다.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  EE는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)를 실행 합니다. `IDebugProperty2` 지역 변수, 기본 형식 또는 Visual Studio에 대 한 개체와 같은 식 계산 결과를 설명 하는 메커니즘을 제공 합니다. 그러면 **지역**, **조사식**또는 **직접 실행** 창에 적절 한 정보가 표시 됩니다.

  SP는 정보를 요청 하는 경우 DE에 의해 EE에 제공 됩니다. SP는 다음 인터페이스 및 해당 파생 항목과 같은 주소 및 필드를 설명 하는 인터페이스를 실행 합니다.

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  EE는 이러한 모든 인터페이스를 사용 합니다.

## <a name="in-this-section"></a>섹션 내용
 [식 계산기 구현 전략](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) 식 계산기 (EE) 구현 전략에 대 한 3 단계 프로세스를 정의 합니다.

## <a name="see-also"></a>추가 정보
- [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

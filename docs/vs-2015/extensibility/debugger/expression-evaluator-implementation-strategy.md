---
title: 식 계산기 구현 전략 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9c2ded111c371fc1a42c8f1ee08769f5b06aeda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842114"
---
# <a name="expression-evaluator-implementation-strategy"></a>식 계산기 구현 전략
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.  
  
 식 계산기 (EE)를 신속 하 게 만드는 방법 중 하나는 **지역 창에서 지역 변수** 를 표시 하는 데 필요한 최소한의 코드를 먼저 구현 하는 것입니다. **지역** 창의 각 줄에는 지역 변수의 이름, 유형 및 값이 표시 되 고, 3 개는 모두 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 개체로 표시 된다는 것을 인식 하는 것이 유용 합니다. `IDebugProperty2` [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 메서드를 호출 하 여 개체에서 지역 변수의 이름, 형식 및 값을 가져올 수 있습니다. **지역 창에서** 지역 변수를 표시 하는 방법에 대 한 자세한 내용은 [지역 표시](../../extensibility/debugger/displaying-locals.md)를 참조 하세요.  
  
## <a name="discussion"></a>토론(Discussion)  
 구현 시퀀스는 [Idebugexpressionevaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)를 구현 하 여 시작 합니다. [구문 분석](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 및 [getmethodproperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 메서드는 지역를 표시 하기 위해 구현 해야 합니다. 를 호출 하면 `IDebugExpressionEvaluator::GetMethodProperty` `IDebugProperty2` 메서드를 나타내는 개체 즉, [Idebugmethodfield](../../extensibility/debugger/reference/idebugmethodfield.md) 개체가 반환 됩니다. 메서드 자체는 **지역** 창에 표시 되지 않습니다.  
  
 다음에는 [Enumchildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 메서드를 구현 해야 합니다. DE (디버그 엔진)는이 메서드를 호출 하 여 `IDebugProperty2::EnumChildren` 의 인수를 전달 함으로써 지역 변수 및 인수 목록을 가져옵니다 `guidFilter` `guidFilterLocalsPlusArgs` . `IDebugProperty2::EnumChildren` 는 [Enumarguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) 및 [enumarguments](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)을 호출 하 여 결과를 단일 열거형으로 결합 합니다. 자세한 내용은 [지역 표시](../../extensibility/debugger/displaying-locals.md) 를 참조 하세요.  
  
## <a name="see-also"></a>참고 항목  
 [식 계산기 구현](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [로컬 항목 표시](../../extensibility/debugger/displaying-locals.md)

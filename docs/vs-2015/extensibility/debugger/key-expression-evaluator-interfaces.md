---
title: 키 식 계산기 인터페이스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b9c01c59e732b777967cf49a61f17305f666325f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841771"
---
# <a name="key-expression-evaluator-interfaces"></a>Key 식 계산기 인터페이스
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.  
  
 식 계산기 (EE)를 계산 컨텍스트와 함께 작성할 때 다음 인터페이스에 대해 잘 알고 있어야 합니다.  
  
## <a name="interface-descriptions"></a>인터페이스 설명  
  
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     에는 현재 실행 지점을 나타내는 데이터 구조를 가져오는 단일 메서드인 [Getaddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md)가 있습니다. 이 데이터 구조는 디버그 엔진 (DE)이 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 메서드에 전달 하 여 식을 계산 하는 세 개의 인수 중 하나입니다. 이 인터페이스는 일반적으로 기호 공급자에 의해 구현 됩니다.  
  
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     에는 기호에 대 한 현재 값을 포함 하는 메모리 영역을 가져오는 [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) 메서드가 있습니다. [Idebugobject](../../extensibility/debugger/reference/idebugobject.md) 개체로 표시 되는 포함 하는 메서드와 [idebugobject](../../extensibility/debugger/reference/idebugfield.md) 개체로 표시 되는 기호 자체를 모두 지정 하면 `IDebugBinder::Bind` 기호 값을 반환 합니다. `IDebugBinder` 는 일반적으로 DE에 의해 구현 됩니다.  
  
- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     단순 데이터 형식을 나타냅니다. 배열 및 메서드와 같은 보다 복잡 한 형식에 대해서는 각각 파생 된 [Idebugarrayfield](../../extensibility/debugger/reference/idebugarrayfield.md) 및 [idebugarrayfield](../../extensibility/debugger/reference/idebugmethodfield.md) 인터페이스를 사용 합니다. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) 는 메서드 또는 클래스와 같은 다른 기호를 포함 하는 기호를 나타내는 또 다른 중요 한 파생 인터페이스입니다. `IDebugField`인터페이스 (및 해당 파생 인터페이스)는 일반적으로 기호 공급자에 의해 구현 됩니다.  
  
     개체를 사용 하 여 `IDebugField` 기호 이름 및 유형을 찾고, [Idebugbinder](../../extensibility/debugger/reference/idebugbinder.md) 개체와 함께 해당 값을 찾을 수 있습니다.  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     기호의 런타임 값에 대 한 실제 비트를 나타냅니다. [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) 는 기호를 나타내는 [idebugfield](../../extensibility/debugger/reference/idebugfield.md) 개체를 사용 하 고 [idebugfield](../../extensibility/debugger/reference/idebugobject.md) 개체를 반환 합니다. [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) 메서드는 메모리 버퍼에서 기호 값을 반환 합니다. DE는 일반적으로이 인터페이스를 구현 하 여 메모리의 속성 값을 나타냅니다.  
  
- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     이 인터페이스는 식 계산기 자체를 나타냅니다. 키 메서드는 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 인터페이스를 반환 하는 [구문 분석](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)입니다.  
  
- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     이 인터페이스는 평가할 준비가 된 구문 분석 된 식을 나타냅니다. 키 메서드는 식의 값과 형식을 나타내는 IDebugProperty2을 반환 하는 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 입니다.  
  
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     이 인터페이스는 값 및 해당 형식을 나타내며 식 계산의 결과입니다.  
  
## <a name="see-also"></a>참고 항목  
 [평가 컨텍스트](../../extensibility/debugger/evaluation-context.md)

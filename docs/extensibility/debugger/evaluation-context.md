---
title: 평가 컨텍스트 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e3d02bd652d6c46b5aabe00e049e425f0921c27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738807"
---
# <a name="evaluation-context"></a>평가 컨텍스트
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.

 DE (디버그 엔진)가 EE (식 계산기)를 호출할 때 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 에 전달 되는 세 개의 인수는 다음 표에 나와 있는 것 처럼 기호를 찾아 평가 하기 위한 컨텍스트를 결정 합니다.

## <a name="arguments"></a>인수

|인수|설명|
|--------------|-----------------|
|`pSymbolProvider`|기호를 식별 하는 데 사용할 기호 처리기 (SH)를 지정 하는 [Idebugsymbol 공급자](../../extensibility/debugger/reference/idebugsymbolprovider.md) 인터페이스입니다.|
|`pAddress`|현재 실행 지점을 지정 하는 [Idebugaddress](../../extensibility/debugger/reference/idebugaddress.md) 인터페이스입니다. 이 인터페이스는 실행 중인 코드가 포함 된 메서드를 찾습니다.|
|`pBinder`|이름이 지정 된 경우 기호의 값과 형식을 찾는 [Idebugbinder](../../extensibility/debugger/reference/idebugbinder.md) 인터페이스입니다.|

 `IDebugParsedExpression::EvaluateSync` 결과 값과 해당 형식을 나타내는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스를 반환 합니다.

## <a name="see-also"></a>참조
- [키 식 계산기 인터페이스](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [지역 표시](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

---
title: 평가 컨텍스트 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738807"
---
# <a name="evaluation-context"></a>평가 컨텍스트
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 계산기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 DEBug 엔진(DE)이 식 계산기(EE)를 호출할 때 [EvaluateSync에](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 전달되는 세 개의 인수는 다음 표와 같이 기호를 찾고 평가하기 위한 컨텍스트를 결정합니다.

## <a name="arguments"></a>인수

|인수|설명|
|--------------|-----------------|
|`pSymbolProvider`|기호를 식별하는 데 사용할 기호 처리기(SH)를 지정하는 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) 인터페이스입니다.|
|`pAddress`|현재 실행 지점을 지정하는 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) 인터페이스입니다. 이 인터페이스는 실행 중인 코드를 포함하는 메서드를 찾습니다.|
|`pBinder`|이름에 지정된 기호의 값과 형식을 찾는 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) 인터페이스입니다.|

 `IDebugParsedExpression::EvaluateSync`결과 값 과 해당 형식을 나타내는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스를 반환합니다.

## <a name="see-also"></a>참조
- [키 표현식 평가기 인터페이스](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [지역 주민 표시](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

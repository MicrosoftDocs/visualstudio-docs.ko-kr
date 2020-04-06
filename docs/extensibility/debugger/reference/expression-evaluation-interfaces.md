---
title: 표현식 평가 인터페이스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da230a2da87b2dd3e3a85ce3ec6c914e829ccc61
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736948"
---
# <a name="expression-evaluation-interfaces"></a>Expression Evaluation Interfaces
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 평가기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 평가기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 다음은 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 디버깅 SDK에 대한 식 평가 인터페이스입니다.

## <a name="discussion"></a>토론
 이러한 인터페이스는 중단 모드 중에 호출 스택의 식을 평가하는 데 사용됩니다. 공통 언어 런타임 식 평가기(EE)에 대해서만 구현됩니다.

 표의 각 인터페이스는 다음 목록에서 구현할 수 있는 구성 요소를 보여 줍니다.

- 디버그 엔진 (DE)

- 식 평가기(EE)

- 비주얼 스튜디오 (VS)

|인터페이스|에 의해 구현|설명|
|---------------|--------------------|-----------------|
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|변수에 대한 숫자 별칭을 나타냅니다.|
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|변수에 대한 숫자 별칭을 나타내고 식 계산기(EE)가 별칭에 대한 응용 프로그램 도메인을 가져올 수 있도록 합니다.|
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|배열 개체를 나타냅니다.|
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|관리되는 배열 개체를 나타내고 식 평가기(EE)가 배열에 대한 기본 인덱스(하한)를 결정할 수 있습니다.|
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|디버그 기호를 메모리의 실제 주소에 바인딩하는 바인더를 나타냅니다.|
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 인터페이스와 동일하지만 형식, 별칭 및 사용자 지정 시각화 도우미에 대한 액세스를 제공합니다.|
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|식 계산기를 나타냅니다.|
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|식 계산기(EE)의 향상된 버전을 나타냅니다.|
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|향상된 파서 트리가 있는 식 계산기(EE)를 나타냅니다.|
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|함수를 나타냅니다.|
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|함수를 나타내고 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 인터페이스를 향상시킵니다.|
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|식 계산기(EE)가 디버거의 출력 창에 메시지를 표시할 수 있도록 합니다.|
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|관리되는 코드 개체를 나타냅니다.|
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|메모리 주소에 바인딩된 기호를 나타내는 기본 인터페이스입니다.|
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스와 동일하지만 추가 정보에 대한 액세스를 제공합니다.|
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|평가할 준비가 된 구문 분석식을 나타냅니다.|
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|포인터를 나타냅니다.|
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|구문 분석 트리에서 포인터를 나타내고 **IDebugPointerObject** 인터페이스를 확장합니다.|
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|형식 시각화 도우미를 통해 형식의 값을 수정하는 기능을 제공합니다.|
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|사용자 지정 뷰어 및 유형 시각화 도우미에 대한 액세스를 제공합니다.|
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) 개체를 만드는 기능을 제공합니다.|
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 개체의 컬렉션을 나타냅니다.|

## <a name="see-also"></a>참조
- [API 참조](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [CLR 식 계산기 작성](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [형식 시각화 도우미 및 사용자 지정 뷰어](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

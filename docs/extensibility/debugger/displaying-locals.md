---
title: 지역 주민 표시 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d44b276aeb9c6acb0ef34cc186662d49246de7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738936"
---
# <a name="display-locals"></a>지역 주민 표시
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 계산기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 실행은 항상 포함 메서드 또는 현재 메서드라고도 하는 메서드의 컨텍스트 내에서 수행됩니다. 실행이 일시 중지되면 Visual Studio는 DE(디버그 엔진)를 호출하여 메서드의 지역 변수 및 인수 목록을 가져옵니다. Visual Studio는 이러한 지역 주민과 해당 값을 **지역 주민** 창에 표시합니다.

 지역 을 표시 하기 위해 DE EE에 속하는 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 메서드를 호출 하 고 평가 컨텍스트, 즉, 기호 공급자 (SP), 현재 실행 주소 및 바인더 개체를 제공 합니다. 자세한 내용은 [평가 컨텍스트](../../extensibility/debugger/evaluation-context.md)를 참조하십시오. 호출이 성공하면 `IDebugExpressionEvaluator::GetMethodProperty` 메서드는 현재 실행 주소를 포함하는 메서드를 나타내는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 개체를 반환합니다.

 DE는 [EnumChildren를](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 호출하여 지역 주민만 반환하도록 필터링되고 [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) 구조 목록을 생성하도록 열거된 [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 개체를 가져옵니다. 각 구조에는 로컬의 이름, 형식 및 값이 포함됩니다. 형식과 값은 형식이 지정된 문자열로 저장되어 표시에 적합합니다. 이름, 유형 및 값은 일반적으로 **지역구** 창의 한 줄에 함께 표시됩니다.

> [!NOTE]
> **QuickWatch** 및 **Watch** 창에는 이름, 값 및 유형이 동일한 변수도 표시됩니다. 그러나 이러한 값은 `IDebugProperty2::EnumChildren`대신 [GetPropertyInfo를](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 호출하여 가져옵니다.

## <a name="in-this-section"></a>섹션 내용
 [지역 주민의 샘플 구현](../../extensibility/debugger/sample-implementation-of-locals.md) 예제를 사용하여 지역 주민을 구현하는 프로세스를 단계별로 실행합니다.

## <a name="related-sections"></a>관련 단원
 [평가 컨텍스트](../../extensibility/debugger/evaluation-context.md) DEBug 엔진(DE)이 식 계산기(EE)를 호출할 때 세 개의 인수를 전달한다고 설명합니다.

## <a name="see-also"></a>참조
 [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

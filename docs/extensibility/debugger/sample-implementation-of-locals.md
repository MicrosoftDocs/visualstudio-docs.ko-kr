---
title: 로컬 샘플 구현 Microsoft Docs
description: Visual Studio가 이 문서의 식 계산기에서 메서드의 로컬을 가져오는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ac52f1524c4be2e4a7afcbd21fb437977fb663e3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902282"
---
# <a name="sample-implementation-of-locals"></a>로컬 샘플 구현
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현하는 이 방법은 더 이상 사용되지 않습니다. CLR 식 계산기를 구현하는 방법에 관한 자세한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리형 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조하세요.

 다음은 Visual Studio가 EE(식 계산기)에서 메서드의 로컬을 가져오는 방법에 관한 개요입니다.

1. Visual Studio는 DE(디버그 엔진) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)를 호출하여 로컬을 포함한 스택 프레임의 모든 속성을 나타내는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 개체를 가져옵니다.

2. `IDebugStackFrame2::GetDebugProperty`는 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)를 호출하여 중단점이 발생한 메서드를 설명하는 개체를 가져옵니다. DE는 기호 공급자([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), 주소([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)), 바인더([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md))를 제공합니다.

3. `IDebugExpressionEvaluator::GetMethodProperty`는 [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)를 제공된 `IDebugAddress` 개체와 함께 호출하여 지정된 주소를 포함하는 메서드를 나타내는 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md)를 가져옵니다.

4. `IDebugContainerField` 인터페이스는 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) 인터페이스를 쿼리합니다. 이 인터페이스는 메서드의 로컬에 대한 액세스를 제공합니다.

5. `IDebugExpressionEvaluator::GetMethodProperty`는 `IDebugProperty2`를 실행하여 메서드의 로컬을 나타내는 클래스(샘플에서 `CFieldProperty`라고 함)를 인스턴스화합니다. `IDebugMethodField` 개체는 `IDebugSymbolProvider`, `IDebugAddress`, `IDebugBinder` 개체와 함께 이 `CFieldProperty` 개체에 배치됩니다.

6. `CFieldProperty` 개체가 초기화되면 `IDebugMethodField` 개체에서 [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md)가 호출되어 메서드 자체에 관한 표시 가능한 모든 정보를 포함하는 [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) 구조체를 가져옵니다.

7. `IDebugExpressionEvaluator::GetMethodProperty`는 `CFieldProperty` 개체를 `IDebugProperty2` 개체로 반환합니다.

8. Visual Studio는 반환된 `IDebugProperty2`에서 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)을 필터 `guidFilterLocalsPlusArgs`와 함께 호출하여 메서드의 로컬을 포함하는 [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 개체를 반환합니다. 이 열거형은 [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) 및 [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) 호출을 통해 채워집니다.

9. Visual Studio는 [Next](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)를 호출하여 각 로컬의 [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) 구조체를 가져옵니다. 이 구조체에는 로컬의 `IDebugProperty2` 인터페이스에 대한 포인터가 포함됩니다.

10. Visual Studio는 로컬별로 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)를 호출하여 로컬의 이름, 값, 형식을 가져옵니다. 이 정보는 **로컬** 창에 표시됩니다.

## <a name="in-this-section"></a>단원 내용
 [GetMethodProperty 구현](../../extensibility/debugger/implementing-getmethodproperty.md) [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 구현을 설명합니다.

 [로컬 열거](../../extensibility/debugger/enumerating-locals.md) DE(디버그 엔진)가 로컬 변수 또는 인수를 열거하기 위해 호출을 수행하는 방법을 설명합니다.

 [로컬 속성 가져오기](../../extensibility/debugger/getting-local-properties.md) DE가 하나 이상 로컬의 이름, 형식, 값을 가져오기 위해 호출을 수행하는 방법을 설명합니다.

 [로컬 값 가져오기](../../extensibility/debugger/getting-local-values.md) 평가 컨텍스트에 의해 제공된 바인더 개체의 서비스가 필요한 로컬의 값을 가져오는 방법을 설명합니다.

 [로컬 평가](../../extensibility/debugger/evaluating-locals.md) 로컬을 평가하는 방법을 설명합니다.

## <a name="related-sections"></a>관련 단원
 [평가 컨텍스트](../../extensibility/debugger/evaluation-context.md) DE가 EE(식 계산기)를 호출할 때 전달되는 인수를 제공합니다.

 [MyCEE 샘플](/previous-versions/) MyC 언어의 식 계산기를 만드는 한 가지 구현 접근 방식을 보여 줍니다.

## <a name="see-also"></a>참조
- [로컬 표시](../../extensibility/debugger/displaying-locals.md)
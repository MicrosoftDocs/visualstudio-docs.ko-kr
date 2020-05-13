---
title: 지역 주민 샘플 구현 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b70e0f9091d40ed6b5fc44934606f42ccd84b21
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713081"
---
# <a name="sample-implementation-of-locals"></a>지역 주민의 샘플 구현
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 계산기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 다음은 Visual Studio에서 식 계산기(EE)에서 메서드에 대한 로컬 메서드를 얻는 방법에 대한 개요입니다.

1. Visual Studio는 디버그 엔진의 (DE) [GetDebugProperty를](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) 호출하여 지역 주민을 포함하여 스택 프레임의 모든 속성을 나타내는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 개체를 가져옵니다.

2. `IDebugStackFrame2::GetDebugProperty`[호출 GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 중단점이 발생 하는 메서드를 설명 하는 개체를 가져옵니다. DE는 기호[공급자(IDebugSymbolProvider),](../../extensibility/debugger/reference/idebugsymbolprovider.md)[주소(IDebugAddress)](../../extensibility/debugger/reference/idebugaddress.md)및[바인더(IDebugBinder)를](../../extensibility/debugger/reference/idebugbinder.md)제공합니다.

3. `IDebugExpressionEvaluator::GetMethodProperty`지정된 주소를 포함하는 메서드를 나타내는 [IDebugContainerField를](../../extensibility/debugger/reference/idebugcontainerfield.md) 얻으려면 제공된 `IDebugAddress` 개체와 [GetContainerField를](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) 호출합니다.

4. 인터페이스는 `IDebugContainerField` [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) 인터페이스에 대해 쿼리됩니다. 메서드의 지역 주민에 대 한 액세스를 제공 하는이 인터페이스입니다.

5. `IDebugExpressionEvaluator::GetMethodProperty`메서드의 지역 을 나타내는 `CFieldProperty` 인터페이스를 `IDebugProperty2` 실행 하는 클래스 (샘플에서 호출)를 인스턴스화 합니다. 개체는 `IDebugMethodField` `CFieldProperty` `IDebugSymbolProvider`의 이 `IDebugAddress`및 개체와 `IDebugBinder` 함께 이 개체에 배치됩니다.

6. 개체가 `CFieldProperty` 초기화되면 [GetInfo는](../../extensibility/debugger/reference/idebugfield-getinfo.md) `IDebugMethodField` 메서드 자체에 대한 모든 표시 가능한 정보를 포함하는 [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) 구조를 얻기 위해 개체에 호출됩니다.

7. `IDebugExpressionEvaluator::GetMethodProperty`개체를 `CFieldProperty` 개체로 `IDebugProperty2` 반환합니다.

8. Visual Studio는 메서드의 지역 `IDebugProperty2` 정보를 포함하는 `guidFilterLocalsPlusArgs` [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 개체를 반환하는 필터를 사용하여 반환된 개체에서 [EnumChildren를](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 호출합니다. 이 열거형은 [에이너시너스와](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) [에이너스 인수에 대한 호출로 채워져 있습니다.](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)

9. Visual Studio 호출 [다음에](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) 각 로컬에 대 한 [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) 구조를 가져옵니다. 이 구조에는 로컬에 `IDebugProperty2` 대한 인터페이스에 대한 포인터가 포함되어 있습니다.

10. Visual Studio는 로컬의 이름, 값 및 형식을 얻기 위해 각 로컬에 대해 [GetPropertyInfo를](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 호출합니다. 이 정보는 지역 **창에** 표시됩니다.

## <a name="in-this-section"></a>섹션 내용
 [GetMethodProperty 구현](../../extensibility/debugger/implementing-getmethodproperty.md) [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)의 구현에 대해 설명합니다.

 [지역 주민 을 모그제](../../extensibility/debugger/enumerating-locals.md) DEBug 엔진(DE)이 지역 변수 또는 인수를 열거하기 위해 호출하는 방법을 설명합니다.

 [로컬 속성 받기](../../extensibility/debugger/getting-local-properties.md) DE가 하나 이상의 지역 주민의 이름, 유형 및 값을 얻기 위해 호출하는 방법을 설명합니다.

 [로컬 값 받기](../../extensibility/debugger/getting-local-values.md) 평가 컨텍스트에서 제공하는 바인더 개체의 서비스가 필요한 로컬 값을 가져오는 것에 대해 설명합니다.

 [지역 주민 평가](../../extensibility/debugger/evaluating-locals.md) 지역 주민의 평가 방법을 설명합니다.

## <a name="related-sections"></a>관련 단원
 [평가 컨텍스트](../../extensibility/debugger/evaluation-context.md) DE가 식 계산기(EE)를 호출할 때 전달되는 인수를 제공합니다.

 [MyCEE 샘플](https://msdn.microsoft.com/library/624a018b-9179-402f-9d48-3aec87b48f4f) MyC 언어에 대한 식 계산기를 만드는 하나의 구현 방법을 보여 줍니다.

## <a name="see-also"></a>참조
- [지역 주민 표시](../../extensibility/debugger/displaying-locals.md)

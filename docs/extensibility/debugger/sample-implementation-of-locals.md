---
title: 지역 |의 샘플 구현 Microsoft Docs
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
ms.openlocfilehash: 86aacb096001bdf634fe019ae9a28f01745c3ce0
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011894"
---
# <a name="sample-implementation-of-locals"></a>로컬의 샘플 구현
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.

 다음은 Visual Studio에서 식 계산기 (EE)의 메서드에 대 한 로컬를 가져오는 방법에 대 한 개요입니다.

1. Visual Studio는 디버그 엔진의 DE (DE) [Getdebugproperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) 를 호출 하 여 로컬을 비롯 한 스택 프레임의 모든 속성을 나타내는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 개체를 가져옵니다.

2. `IDebugStackFrame2::GetDebugProperty`[Getmethodproperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 를 호출 하 여 중단점이 발생 한 메서드를 설명 하는 개체를 가져옵니다. DE는 기호 공급자 ([idebugsymbol 공급자](../../extensibility/debugger/reference/idebugsymbolprovider.md)), 주소 ([idebugaddress](../../extensibility/debugger/reference/idebugaddress.md)) 및 바인더 ([idebugbinder](../../extensibility/debugger/reference/idebugbinder.md))를 제공 합니다.

3. `IDebugExpressionEvaluator::GetMethodProperty` 제공 된 개체를 사용 하 여 [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) 를 호출 `IDebugAddress` 하 여 지정 된 주소를 포함 하는 메서드를 나타내는 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) 를 가져옵니다.

4. `IDebugContainerField` [Idebugmethodfield](../../extensibility/debugger/reference/idebugmethodfield.md) 인터페이스에 대해 인터페이스를 쿼리 합니다. 이 인터페이스는 메서드의 지역에 대 한 액세스를 제공 합니다.

5. `IDebugExpressionEvaluator::GetMethodProperty``CFieldProperty` `IDebugProperty2` 메서드 지역을 나타내기 위해 인터페이스를 실행 하는 클래스 (샘플에서 호출 됨)를 인스턴스화합니다. `IDebugMethodField`개체는 `CFieldProperty` `IDebugSymbolProvider` , `IDebugAddress` 및 개체와 함께이 개체에 배치 됩니다 `IDebugBinder` .

6. `CFieldProperty`개체가 초기화 되 면 개체에 대해 [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) 가 호출 되어 `IDebugMethodField` 메서드 자체에 대해 표시 가능한 모든 정보를 포함 하는 [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) 구조를 가져옵니다.

7. `IDebugExpressionEvaluator::GetMethodProperty` 개체를 `CFieldProperty` 개체로 반환 합니다 `IDebugProperty2` .

8. Visual Studio는 반환 된 개체의 [Enumchildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) `IDebugProperty2` 을 필터와 함께 호출 합니다 `guidFilterLocalsPlusArgs` .이 필터는 메서드의 지역을 포함 하는 [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 개체를 반환 합니다. 이 열거형은 [enumlocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) 및 [enumlocals](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)에 대 한 호출로 채워집니다.

9. Visual Studio는 [다음](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) 을 호출 하 여 각 로컬에 대 한 [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) 구조를 가져옵니다. 이 구조체는 `IDebugProperty2` 로컬의 인터페이스에 대 한 포인터를 포함 합니다.

10. Visual Studio는 로컬의 이름, 값 및 형식을 가져오기 위해 각 로컬에 대해 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 를 호출 합니다. 이 정보는 **지역** 창에 표시 됩니다.

## <a name="in-this-section"></a>섹션 내용
 [GetMethodProperty 구현](../../extensibility/debugger/implementing-getmethodproperty.md) [Getmethodproperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)의 구현을 설명 합니다.

 [지역 열거](../../extensibility/debugger/enumerating-locals.md) 디버그 엔진 (DE)에서 지역 변수 또는 인수를 열거 하는 호출을 수행 하는 방법을 설명 합니다.

 [로컬 속성 가져오기](../../extensibility/debugger/getting-local-properties.md) 제거를 호출 하 여 하나 이상의 지역에 대 한 이름, 형식 및 값을 가져오는 방법을 설명 합니다.

 [로컬 값 가져오기](../../extensibility/debugger/getting-local-values.md) 계산 컨텍스트에서 지정 하는 바인더 개체의 서비스가 필요한 로컬의 값을 가져오는 방법을 설명 합니다.

 [지역 평가](../../extensibility/debugger/evaluating-locals.md) 로컬을 평가 하는 방법을 설명 합니다.

## <a name="related-sections"></a>관련 단원
 [평가 컨텍스트](../../extensibility/debugger/evaluation-context.md) DE가 식 계산기 (EE)를 호출할 때 전달 되는 인수를 제공 합니다.

 [MyCEE 샘플](/previous-versions/) MyC 언어에 대 한 식 계산기를 만드는 한 가지 구현 방법을 보여 줍니다.

## <a name="see-also"></a>참고 항목
- [지역 표시](../../extensibility/debugger/displaying-locals.md)
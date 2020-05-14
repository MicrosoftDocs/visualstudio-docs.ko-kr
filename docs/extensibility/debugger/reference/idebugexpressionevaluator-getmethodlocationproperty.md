---
title: IDebug표현평가자::GetMethodLocationProperty | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6ba87d6c1a1f7370ce5e209440589f362b87035
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729525"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
이 메서드는 메서드 위치를 변환하고 오프셋을 메모리 주소로 변환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetMethodLocationProperty( 
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodLocationProperty(
   string               upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>매개 변수
`upstrFullyQualifiedMethodPlusOffset`\
【인】 문자열로 표현된 메서드 위치 및 오프셋입니다.

`pSymbolProvider`\
【인】 [IDebugSymbol공급자](../../../extensibility/debugger/reference/idebugsymbolprovider.md) 개체로 표현된 기호 공급자입니다.

`pAddress`\
【인】 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 개체로 표현되는 메서드 내의 주소입니다.

`pBinder`\
【인】 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 개체로 표현된 바인더입니다.

`ppProperty`\
【아웃】 메모리 주소를 나타내는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 반환된 주소를 사용하여 중단점을 설정할 수 있습니다.

 이름에도 `upstrFullyQualifiedMethodPlusOffset`불구하고 이 매개 변수는 부분적으로 정규화된 메서드 이름을 전달할 수 있습니다. 이 경우 선택한 메서드는 를 둘러싸는 `pAddress`메서드입니다. 이 매개 변수를 해석하는 방법은 식 계산기의 구현과 해당 매개 변수가 지원하는 언어에 달려 있습니다.

## <a name="see-also"></a>참조
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)

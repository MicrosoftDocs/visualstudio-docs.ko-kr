---
title: IDebug표현평가자::겟메소드속성 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ebcf24ee39505091ff79c1f2f31d505217f77efb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729510"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
이 메서드는 메서드의 지역 정보, 인수 및 기타 속성을 포함하는 속성 개체를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetMethodProperty( 
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BOOL                  fIncludeHiddenLocals,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodProperty(
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   int                  fIncludeHiddenLocals,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>매개 변수
`pSymbolProvider`\
【인】 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) 개체로 표현되는 사용할 기호 공급자입니다.

`pAddress`\
【인】 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 개체로 표현되는 코드의 주소는 가장 가까운 포함 함수로 해결해야 합니다.

`pBinder`\
【인】 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 개체로 표현되는 사용할 바인더입니다.

`fIncludeHiddenLocals`\
【인】 Nonzero`TRUE`()는 숨겨진 지역 주민을 포함하는 것을 의미합니다. 0`FALSE`() 숨겨진 지역 주민을 떠나는 것을 의미합니다.

`ppProperty`\
【아웃】 메서드를 나타내는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 숨겨진 지역 변수는 일반적으로 컴파일러에서 생성되는 변수입니다.

## <a name="see-also"></a>참조
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

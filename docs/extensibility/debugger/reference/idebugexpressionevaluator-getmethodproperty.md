---
title: 'IDebugExpressionEvaluator:: GetMethodProperty | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729510"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
이 메서드는 지역, 인수 및 메서드의 기타 속성을 포함 하는 속성 개체를 가져옵니다.

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
진행 [Idebugsymbol 공급자](../../../extensibility/debugger/reference/idebugsymbolprovider.md) 개체로 표시 되는 사용할 기호 공급자입니다.

`pAddress`\
진행 가장 가까운 포함 함수로 확인 되어야 하는 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 개체로 표시 되는 코드의 주소입니다.

`pBinder`\
진행 [Idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md) 개체로 표시 되는 사용할 바인더입니다.

`fIncludeHiddenLocals`\
진행 0이 아닌 `TRUE` 값 ()은 숨겨진 로컬을 포함 하는 것을 의미 합니다. 0 ( `FALSE` )은 숨겨진 로컬을 생략 합니다.

`ppProperty`\
제한이 메서드를 나타내는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 숨겨진 로컬은 일반적으로 컴파일러에 의해 생성 되는 변수입니다.

## <a name="see-also"></a>추가 정보
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

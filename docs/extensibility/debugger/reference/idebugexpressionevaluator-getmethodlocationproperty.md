---
description: 이 메서드는 메서드 위치와 오프셋을 메모리 주소로 변환 합니다.
title: 'IDebugExpressionEvaluator:: GetMethodLocationProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ddc9c17b90be6d65786d58ff2bf585461c4fc69f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092191"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
이 메서드는 메서드 위치와 오프셋을 메모리 주소로 변환 합니다.

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
진행 문자열로 표현 된 메서드 위치 및 오프셋입니다.

`pSymbolProvider`\
진행 [Idebugsymbol 공급자](../../../extensibility/debugger/reference/idebugsymbolprovider.md) 개체로 표시 되는 기호 공급자입니다.

`pAddress`\
진행 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 개체로 표시 되는 메서드 내의 주소입니다.

`pBinder`\
진행 [Idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md) 개체로 표시 되는 바인더입니다.

`ppProperty`\
제한이 메모리 주소를 나타내는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 반환 된 주소는 중단점을 설정 하는 데 사용할 수 있습니다 (예:).

 이름에도 불구 `upstrFullyQualifiedMethodPlusOffset` 하 고이 매개 변수는 부분적으로 정규화 된 메서드 이름으로 전달 될 수 있습니다. 이 경우 선택한 메서드가를 포함 하는 메서드입니다 `pAddress` . 이 매개 변수를 해석 하는 방법은 식 계산기 및 지원 되는 언어의 구현에 따라 결정 됩니다.

## <a name="see-also"></a>참조
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)

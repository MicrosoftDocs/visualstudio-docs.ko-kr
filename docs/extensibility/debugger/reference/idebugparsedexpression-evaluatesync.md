---
title: IDebugparsed표현식::평가동기화 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f00b209ff5f91d160e89f5f55ad966fbe9e6414
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726015"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
이 메서드는 구문 분석된 식을 평가 하 고 선택적으로 다른 데이터 형식에 결과 캐스팅 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EvaluateSync( 
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BSTR                  bstrResultType,
   IDebugProperty2**     ppResult
);
```

```csharp
int EvaluateSync(
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   string               bstrResultType,
   out IDebugProperty2  ppResult
);
```

## <a name="parameters"></a>매개 변수
`dwEvalFlags`\
【인】 식을 평가하는 방법을 제어하는 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 상수의 조합입니다.

`dwTimeout`\
【인】 이 메서드에서 반환하기 전에 기다릴 최대 시간(밀리초)을 지정합니다. 무기한 `INFINITE` 대기하는 데 사용합니다.

`pSymbolProvider`\
【인】 [IDebugSymbol공급자](../../../extensibility/debugger/reference/idebugsymbolprovider.md) 인터페이스로 표현된 기호 공급자입니다.

`pAddress`\
【인】 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 인터페이스로 표현된 메서드 내의 현재 실행 위치입니다.

`pBinder`\
【인】 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 인터페이스로 표현된 바인더입니다.

`bstrResultType`\
【인】 결과를 캐스팅해야 하는 형식을 입력합니다. 이 인수는 null 값이 될 수 있습니다.

`ppResult`\
【아웃】 평가 결과를 나타내는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 식 평가 컨텍스트는 `pAddress`포함 메서드를 결정한 다음 언어 범위 지정 규칙을 사용하여 식에서 기호값을 결정할 수 있는 에 의해 제공됩니다.

## <a name="see-also"></a>참조
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)

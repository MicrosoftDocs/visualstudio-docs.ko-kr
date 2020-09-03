---
title: 'IDebugParsedExpression:: EvaluateSync | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726015"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
이 메서드는 구문 분석 된 식을 계산 하 고 선택적으로 결과를 다른 데이터 형식으로 캐스팅 합니다.

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
진행 식이 계산 되는 방법을 제어 하는 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 상수의 조합입니다.

`dwTimeout`\
진행 이 메서드에서 반환 될 때까지 대기할 최대 시간 (밀리초)을 지정 합니다. `INFINITE`무기한 대기 하려면를 사용 합니다.

`pSymbolProvider`\
진행 [Idebugsymbol 공급자](../../../extensibility/debugger/reference/idebugsymbolprovider.md) 인터페이스로 표시 되는 기호 공급자입니다.

`pAddress`\
진행 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 인터페이스로 표시 되는 메서드 내의 현재 실행 위치입니다.

`pBinder`\
진행 [Idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md) 인터페이스로 표시 되는 바인더입니다.

`bstrResultType`\
진행 결과를 캐스팅할 형식입니다. 이 인수는 null 값일 수 있습니다.

`ppResult`\
제한이 계산 결과를 나타내는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 식 계산 컨텍스트는에 의해 지정 됩니다 .이를 통해 포함 하는 `pAddress` 메서드를 확인 한 다음 언어 범위 지정 규칙을 사용 하 여 식에서 기호 값을 확인할 수 있습니다.

## <a name="see-also"></a>추가 정보
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)

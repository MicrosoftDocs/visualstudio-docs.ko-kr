---
description: 식 계산 결과를 가져옵니다.
title: 'IDebugExpressionEvaluationCompleteEvent2:: GetResult | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
ms.assetid: d9ad3e22-b6b2-421e-9a43-6bb8c70d12a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f1aaf150f3502490f7580866ac99a9fc16197dde
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092243"
---
# <a name="idebugexpressionevaluationcompleteevent2getresult"></a>IDebugExpressionEvaluationCompleteEvent2::GetResult
식 계산 결과를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetResult( 
   IDebugProperty2** ppResult
);
```

```csharp
int GetResult( 
   out IDebugProperty2 ppResult
);
```

## <a name="parameters"></a>매개 변수
`ppResult` 제한이 식 계산 결과를 나타내는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 반환 된 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 개체는 계산 된 식의 값을 포함 합니다. 이 값은 배열과 같은 복합 값일 수 있지만 최종 결과는 사용자에 게 표시 되는 숫자 또는 문자열 값 이어야 합니다.

## <a name="see-also"></a>참조
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

---
description: 'IDebugFunctionObject:: Evaluate는 함수를 호출 하 고 결과 값을 개체로 반환 합니다.'
title: 'IDebugFunctionObject:: Evaluate | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b9770878040422d96c31fab8d57df468af614e8e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063593"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
함수를 호출 하 고 결과 값을 개체로 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Evaluate( 
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate(
   IDebugObject[]   ppParams,
   IntPtr           dwParams,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>매개 변수
`ppParams`\
진행 입력 매개 변수를 나타내는 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 개체의 배열입니다. 이러한 각 매개 변수는 `Create` [Idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 인터페이스의 메서드 중 하나를 사용 하 여 생성 되었습니다.

`dwParams`\
진행 배열에 있는 매개 변수의 수 `ppParams` 입니다.

`dwTimeout`\
진행 이 메서드에서 반환 될 때까지 대기할 최대 시간 (밀리초)을 지정 합니다. `INFINITE`무기한 대기 하려면를 사용 합니다.

`ppResult`\
제한이 함수 값을 개체로 나타내는 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드는 [Idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 개체로 표시 되는 함수에 대 한 호출을 설정 하 고 실행 합니다.

## <a name="see-also"></a>참조
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)

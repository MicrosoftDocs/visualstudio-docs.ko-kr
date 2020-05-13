---
title: IDebugFunctionObject2::평가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d87d7d3531d198a1478b4aaa55b354c3ac101302
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728443"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
함수를 호출하고 결과 값을 개체로 반환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Evaluate (
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwEvalFlags,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate (
   IDebugObject     ppParams,
   uint             dwParams,
   uint             dwEvalFlags,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>매개 변수
`ppParams`\
【인】 입력 매개 변수를 나타내는 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 개체의 배열입니다. 이러한 각 매개 변수는 이 인터페이스의 Create 메서드 중 하나를 사용하여 만들어졌습니다.

`dwParams`\
【인】 배열의 매개 변수 `ppParams` 수입니다.

`dwEvalFlags`\
【인】 평가를 수행할 방법을 지정하는 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 열거형의 플래그 조합입니다.

`dwTimeout`\
【인】 이 메서드에서 반환하기 전에 기다릴 최대 시간(밀리초)을 지정합니다. **무한을** 사용하여 무기한 기다립니다.

`ppResult`\
【아웃】 함수의 값을 개체로 나타내는 **IDebugObject를** 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)

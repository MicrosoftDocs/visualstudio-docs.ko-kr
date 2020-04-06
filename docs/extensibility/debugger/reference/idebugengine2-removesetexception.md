---
title: IDebugEngine2::제거예외 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e811ce2e387c299ff3655799bf35185c1d2029b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730928"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
디버그 엔진에서 더 이상 처리되지 않도록 지정된 예외를 제거합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT RemoveSetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int RemoveSetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>매개 변수
`pException`\
【인】 제거할 예외를 설명하는 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) 구조입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 제거되는 예외는 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) 메서드에 대한 이전 호출에 의해 이전에 설정된 것이어야 합니다.

 설정된 모든 예외를 한 번에 제거하려면 [RemoveAllSetExceptions 메서드를 호출합니다.](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)

## <a name="see-also"></a>참조
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)

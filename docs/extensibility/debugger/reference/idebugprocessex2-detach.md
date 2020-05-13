---
title: IDebugProcessEx2::D에타흐 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7379436ae0da57d7f8c47ce8484c810a53a0a453
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723365"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
이 메서드는 세션이 더 이상 프로세스를 디버깅하지 않는다는 것을 프로세스에 알립니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Detach( 
   IDebugSession2* pSession
);
```

```csharp
int Detach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>매개 변수
`pSession`\
【인】 이 프로세스를 분리할 세션을 고유하게 식별하는 값입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 전달된 `pSession` 인터페이스는 원래 이 프로세스에 연결된 세션 디버그 관리자를 고유하게 식별하는 값인 쿠키로만 처리됩니다. 제공된 인터페이스의 메서드가 작동하지 않습니다.

## <a name="see-also"></a>참조
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)

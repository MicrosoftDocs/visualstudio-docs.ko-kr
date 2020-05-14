---
title: IDebug예외이벤트2:GetException | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 332cbb28bd175aa5c3b4187ae735a479ba9de6b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729854"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
이 이벤트를 발생시킨 예외에 대한 자세한 설명을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetException( 
   EXCEPTION_INFO* pExceptionInfo
);
```

```csharp
int GetException( 
   EXCEPTION_INFO[] pExceptionInfo
);
```

## <a name="parameters"></a>매개 변수
`pExceptionInfo`\
【인, 아웃】 예외에 대한 설명으로 채워진 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) 구조입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명

 [C++ 전용] 호출자는 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) 구조의 모든 문자열을 해제하고 구조체에서 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 개체를 해제할 책임이 있습니다.

## <a name="see-also"></a>참조
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

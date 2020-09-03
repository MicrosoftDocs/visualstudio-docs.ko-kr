---
title: 'IDebugExceptionEvent2:: GetException | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729854"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
이 이벤트를 발생 시킨 예외에 대 한 자세한 설명을 가져옵니다.

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
[in, out] 예외에 대 한 설명과 함께 채워지는 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) 구조체입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명

 [C + + 전용] 호출자는 구조체에서 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 개체를 해제 하는 것 외에도 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) 구조에서 문자열을 해제 해야 합니다.

## <a name="see-also"></a>추가 정보
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

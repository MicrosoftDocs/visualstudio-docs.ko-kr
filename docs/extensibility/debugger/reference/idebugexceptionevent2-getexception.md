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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0d9b9a174843b4c48dccc00370176668c582b53c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933286"
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

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명

 [C + + 전용] 호출자는 구조체에서 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 개체를 해제 하는 것 외에도 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) 구조에서 문자열을 해제 해야 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

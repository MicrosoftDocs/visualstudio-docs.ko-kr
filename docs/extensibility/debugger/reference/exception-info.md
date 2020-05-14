---
title: EXCEPTION_INFO | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a305d34123d02b1fdbd545a438db4461643ed185
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737026"
---
# <a name="exception_info"></a>EXCEPTION_INFO
디버깅 중인 프로그램에서 throw된 예외 또는 런타임 오류를 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct tagEXCEPTION_INFO {
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    BSTR            bstrExceptionName;
    DWORD           dwCode;
    EXCEPTION_STATE dwState;
    GUID            guidType;
} EXCEPTION_INFO;
```

```csharp
public struct EXCEPTION_INFO {
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public string         bstrExceptionName;
    public uint           dwCode;
    public uint           dwState;
    public Guid           guidType;
};
```

## <a name="members"></a>멤버
`pProgram`\
예외가 발생한 프로그램을 나타내는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 개체입니다.

`bstrProgramName`\
예외가 발생한 프로그램의 이름입니다.

`bstrExceptionName`\
예외의 이름입니다.

`dwCode`\
예외 또는 런타임 오류에 대한 식별 코드입니다.

`dwState`\
예외의 상태를 정의하는 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) 열거형의 값입니다.

`guidType`\
GUID 언어 식별자 `guidLang` 또는 `guidEng`.

## <a name="remarks"></a>설명
이 구조는 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) 및 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) 메서드에 매개 변수로 전달 됩니다. 이 구조는 채울 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) 메서드에도 전달됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
- [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)

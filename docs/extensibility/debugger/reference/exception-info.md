---
title: EXCEPTION_INFO | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737026"
---
# <a name="exception_info"></a>EXCEPTION_INFO
디버깅 중인 프로그램에서 throw 되는 예외 또는 런타임 오류에 대해 설명 합니다.

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
예외가 발생 한 프로그램을 나타내는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 개체입니다.

`bstrProgramName`\
예외가 발생 한 프로그램의 이름입니다.

`bstrExceptionName`\
예외의 이름입니다.

`dwCode`\
예외 또는 런타임 오류에 대 한 id 코드입니다.

`dwState`\
예외의 상태를 정의 하는 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) 열거형의 값입니다.

`guidType`\
GUID 언어 식별자 (또는) `guidLang` `guidEng` 입니다.

## <a name="remarks"></a>설명
이 구조체는 [setexception](../../../extensibility/debugger/reference/idebugengine2-setexception.md) 및 [removesetexception](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) 메서드에 매개 변수로 전달 됩니다. 이 구조체는 채울 [Getexception](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) 메서드에도 전달 됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
- [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)

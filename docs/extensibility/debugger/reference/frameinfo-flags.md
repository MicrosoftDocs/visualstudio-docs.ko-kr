---
title: FRAMEINFO_FLAGS | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3510726400623c5ddf3e7a4d58a4903763b91245
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736806"
---
# <a name="frameinfo_flags"></a>FRAMEINFO_FLAGS
스택 프레임 개체에 대해 검색할 정보를 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
typedef DWORD FRAMEINFO_FLAGS;
```

```csharp
public enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
```

## <a name="fields"></a>필드
`FIF_FUNCNAME`\
`m_bstrFuncName` 필드를 초기화/사용합니다.

`FIF_RETURNTYPE`\
`m_bstrReturnType` 필드를 초기화/사용합니다.

`FIF_ARGS`\
`m_bstrArgs` 필드를 초기화/사용합니다.

`FIF_LANGUAGE`\
`m_bstrLanguage` 필드를 초기화/사용합니다.

`FIF_MODULE`\
`m_bstrModule` 필드를 초기화/사용합니다.

`FIF_STACKRANGE`\
`m_addrMin` 및 `m_addrMax` (스택 범위) 필드를 초기화/사용합니다.

`FIF_FRAME`\
`m_pFrame` 필드를 초기화/사용합니다.

`FIF_DEBUGINFO`\
`m_fHasDebugInfo` 필드를 초기화/사용합니다.

`FIF_STALECODE`\
`m_fStaleCode` 필드를 초기화/사용합니다.

`FIF_ANNOTATEDFRAME`\
`m_fAnnotatedFrame` 필드를 초기화/사용합니다.

`FIF_DEBUG_MODULEP`\
`m_pModule` 필드를 초기화/사용합니다.

`FIF_FUNCNAME_FORMAT`\
함수 이름을 서식을 지정합니다. 결과가 `m_bstrFunName` 필드에 반환되고 다른 필드가 채워지지 않습니다.

`FIF_FUNCNAME_RETURNTYPE`\
필드에 반환 형식을 `m_bstrFuncName` 추가합니다.

`FIF_FUNCNAME_ARGS`\
`m_bstrFuncName` 필드에 인수를 추가합니다.

`FIF_FUNCNAME_LANGUAGE`\
필드에 언어를 추가합니다. `m_bstrFuncName`

`FIF_FUNCNAME_MODULE`\
모듈 이름을 필드에 `m_bstrFuncName` 추가합니다.

`FIF_FUNCNAME_LINES`\
필드에 줄 수를 추가합니다. `m_bstrFuncName`

`FIF_FUNCNAME_OFFSET`\
지정된 경우 `m_bstrFuncName` `FIF_FUNCNAME_LINES` 선의 시작부터 바이트 단위로 오프셋을 필드에 추가합니다. `FIF_FUNCNAME_LINES` 지정되지 않았거나 줄 번호를 사용할 수 없는 경우 함수시작부터 바이트 단위로 오프셋을 추가합니다.

`FIF_FUNCNAME_ARGS_TYPES`\
`m_bstrFuncName` 각 함수 인수의 형식을 필드에 추가합니다.

`FIF_FUNCNAME_ARGS_NAMES`\
`m_bstrFuncName` 각 함수 인수의 이름을 필드에 추가합니다.

`FIF_FUNCNAME_ARGS_VALUES`\
각 함수 인수의 값을 `m_bstrFuncName` 필드에 추가합니다.

`FIF_FUNCNAME_ARGS_ALL`\
`m_bstrFuncName` 모든 인수의 형식, 이름 및 값을 필드에 추가합니다.

`FIF_ARGS_TYPES`\
인수 형식은 검색되고 서식이 지정됩니다.

`FIF_ARGS_NAMES`\
인수 이름은 검색되고 서식이 지정됩니다.

`FIF_ARGS_VALUES`\
인수 값은 검색되고 서식이 지정됩니다.

`FIF_ARGS_ALL`\
모든 인수의 형식, 이름 및 값을 검색하고 서식을 지정합니다.

`FIF_ARGS_NOFORMAT`\
인수의 서식이 지정되지 않도록 지정합니다(예: 인수 목록 주위에 열기 및 닫는 괄호를 추가하거나 인수 간에 구분 기호를 추가하지 마십시오).

`FIF_ARGS_NO_FUNC_EVAL`\
인수 값을 검색할 때 함수(속성) 평가를 사용해서는 안 되도록 지정합니다.

`FIF_FILTER_NON_USER_CODE`\
디버그 엔진은 비사용자 코드 프레임을 필터링하여 포함되지 않도록 하는 것입니다.

`FIF_ARGS_NO_TOSTRING`\
함수 인수를 `ToString()` 반환할 때 함수 평가 또는 서식 지정을 허용하지 마십시오.

`FIF_DESIGN_TIME_EXPR_EVAL`\
프레임 정보는 호스팅 프로세스가 아닌 호스팅된 앱 도메인에서 얻어야 합니다.

## <a name="remarks"></a>설명
이러한 플래그는 [FrameInfo](../../../extensibility/debugger/reference/frameinfo.md) 구조 또는 구조체에서 초기화할 필드를 나타내기 위해 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 및 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) 메서드에 전달됩니다.

이러한 플래그는 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 구조체의 어떤 필드가 사용되고 구조가 반환될 때 유효한지 나타내는 데도 사용됩니다. 이러한 값은 약간 과 `OR`결합될 수 있습니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)

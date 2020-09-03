---
title: FRAMEINFO_FLAGS | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736806"
---
# <a name="frameinfo_flags"></a>FRAMEINFO_FLAGS
스택 프레임 개체에 대해 검색할 정보를 지정 합니다.

## <a name="syntax"></a>Syntax

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
필드를 초기화/사용 `m_bstrFuncName` 합니다.

`FIF_RETURNTYPE`\
필드를 초기화/사용 `m_bstrReturnType` 합니다.

`FIF_ARGS`\
필드를 초기화/사용 `m_bstrArgs` 합니다.

`FIF_LANGUAGE`\
필드를 초기화/사용 `m_bstrLanguage` 합니다.

`FIF_MODULE`\
필드를 초기화/사용 `m_bstrModule` 합니다.

`FIF_STACKRANGE`\
`m_addrMin`및 `m_addrMax` (스택 범위) 필드를 초기화/사용 합니다.

`FIF_FRAME`\
필드를 초기화/사용 `m_pFrame` 합니다.

`FIF_DEBUGINFO`\
필드를 초기화/사용 `m_fHasDebugInfo` 합니다.

`FIF_STALECODE`\
필드를 초기화/사용 `m_fStaleCode` 합니다.

`FIF_ANNOTATEDFRAME`\
필드를 초기화/사용 `m_fAnnotatedFrame` 합니다.

`FIF_DEBUG_MODULEP`\
필드를 초기화/사용 `m_pModule` 합니다.

`FIF_FUNCNAME_FORMAT`\
함수 이름의 형식을 지정 합니다. 결과는 필드에 반환 되 `m_bstrFunName` 고 다른 필드는 채워지지 않습니다.

`FIF_FUNCNAME_RETURNTYPE`\
반환 형식을 필드에 추가 합니다 `m_bstrFuncName` .

`FIF_FUNCNAME_ARGS`\
필드에 인수를 추가 `m_bstrFuncName` 합니다.

`FIF_FUNCNAME_LANGUAGE`\
필드에 언어를 추가 합니다 `m_bstrFuncName` .

`FIF_FUNCNAME_MODULE`\
필드에 모듈 이름을 추가 합니다 `m_bstrFuncName` .

`FIF_FUNCNAME_LINES`\
필드에 줄 수를 추가 합니다 `m_bstrFuncName` .

`FIF_FUNCNAME_OFFSET`\
`m_bstrFuncName`가 지정 된 경우 줄의 시작 부분에서 오프셋 (바이트)을 필드에 추가 합니다 `FIF_FUNCNAME_LINES` . 을 `FIF_FUNCNAME_LINES` 지정 하지 않거나 줄 번호를 사용할 수 없는 경우는 함수의 시작 부분에서 오프셋을 바이트 단위로 추가 합니다.

`FIF_FUNCNAME_ARGS_TYPES`\
각 함수 인수의 형식을 필드에 추가 합니다 `m_bstrFuncName` .

`FIF_FUNCNAME_ARGS_NAMES`\
각 함수 인수의 이름을 필드에 추가 합니다 `m_bstrFuncName` .

`FIF_FUNCNAME_ARGS_VALUES`\
각 함수 인수의 값을 필드에 추가 `m_bstrFuncName` 합니다.

`FIF_FUNCNAME_ARGS_ALL`\
모든 인수의 형식, 이름 및 값을 필드에 추가 합니다 `m_bstrFuncName` .

`FIF_ARGS_TYPES`\
인수 형식이 검색 되 고 형식이 지정 됩니다.

`FIF_ARGS_NAMES`\
인수 이름이 검색 되 고 형식이 지정 됩니다.

`FIF_ARGS_VALUES`\
인수 값이 검색 되 고 형식이 지정 됩니다.

`FIF_ARGS_ALL`\
모든 인수의 형식, 이름 및 값을 검색 하 고 형식을 지정 합니다.

`FIF_ARGS_NOFORMAT`\
인수의 형식을 지정 하지 않도록 지정 합니다. 예를 들어 인수 목록 주위에 여는 괄호와 닫는 괄호를 추가 하거나 인수 사이에 구분 기호를 추가 하지 않습니다.

`FIF_ARGS_NO_FUNC_EVAL`\
인수 값을 검색할 때 함수 (속성) 계산을 사용 하지 않도록 지정 합니다.

`FIF_FILTER_NON_USER_CODE`\
디버그 엔진은 사용자가 제공 하지 않는 코드 프레임을 필터링 하 여 포함 되지 않도록 합니다.

`FIF_ARGS_NO_TOSTRING`\
`ToString()`함수 인수를 반환할 때 함수 실행 또는 서식 지정을 허용 하지 않습니다.

`FIF_DESIGN_TIME_EXPR_EVAL`\
프레임 정보는 호스팅 프로세스가 아닌 호스트 된 앱 도메인에서 가져와야 합니다.

## <a name="remarks"></a>설명
이러한 플래그는 [프레임 정보](../../../extensibility/debugger/reference/frameinfo.md) 구조 또는 구조에서 초기화할 필드를 나타내기 위해 [Enum프레임 정보](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 및 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) 메서드에 전달 됩니다.

이러한 플래그는 사용 되는 [프레임 정보](../../../extensibility/debugger/reference/frameinfo.md) 구조의 필드와 구조가 반환 될 때 유효한 필드를 표시 하는 데도 사용 됩니다. 이러한 값은 비트와 함께 사용할 수 있습니다 `OR` .

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)

---
title: 프레임 정보 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c40361a9739bf468de2038df4325fa1ac98337c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736788"
---
# <a name="frameinfo"></a>FRAMEINFO
스택 프레임을 설명 합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct tagFRAMEINFO {
    FRAMEINFO_FLAGS    m_dwValidFields;
    BSTR               m_bstrFuncName;
    BSTR               m_bstrReturnType;
    BSTR               m_bstrArgs;
    BSTR               m_bstrLanguage;
    BSTR               m_bstrModule;
    UINT64             m_addrMin;
    UINT64             m_addrMax;
    IDebugStackFrame2* m_pFrame;
    IDebugModule2*     m_pModule;
    BOOL               m_fHasDebugInfo;
    BOOL               m_fStaleCode;
    BOOL               m_fAnnotatedFrame;
} FRAMEINFO;
```

```csharp
public struct FRAMEINFO {
    public uint              m_dwValidFields;
    public string            m_bstrFuncName;
    public string            m_bstrReturnType;
    public string            m_bstrArgs;
    public string            m_bstrLanguage;
    public string            m_bstrModule;
    public ulong             m_addrMin;
    public ulong             m_addrMax;
    public IDebugStackFrame2 m_pFrame;
    public IDebugModule2     m_pModule;
    public int               m_fHasDebugInfo;
    public int               m_fStaleCode;
    public int               m_fAnnotatedFrame;
} FRAMEINFO;
```

## <a name="members"></a>멤버
`m_dwValidFields`\
채울 필드를 지정 하는 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) 열거형의 플래그 조합입니다.

`m_bstrFuncName`\
스택 프레임과 연결 된 함수 이름입니다.

`m_bstrReturnType`\
스택 프레임과 연결 된 반환 형식입니다.

`m_bstrArgs`\
스택 프레임과 연결 된 함수에 대 한 인수입니다.

`m_bstrLanguage`\
함수가 구현 되는 언어입니다.

`m_bstrModule`\
스택 프레임과 연결 된 모듈 이름입니다.

`m_addrMin`\
최소 실제 스택 주소입니다.

`m_addrMAX`\
최대 실제 스택 주소입니다.

`m_pFrame`\
이 스택 프레임을 나타내는 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 개체입니다.

`m_pModule`\
이 스택 프레임을 포함 하는 모듈을 나타내는 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 개체입니다.

`m_fHasDebugInfo`\
`TRUE`지정 된 프레임에 디버그 정보가 있는 경우 0이 아닌 ()입니다.

`m_fStaleCode`\
`TRUE`스택 프레임이 더 이상 유효 하지 않은 코드와 연결 되어 있는 경우 0이 아닌 ()입니다.

`m_fAnnotatedFrame`\
`TRUE`세션 디버그 관리자 (SDM)에서 스택 프레임에 주석을 추가 하는 경우 0이 아닙니다.

## <a name="remarks"></a>설명
이 구조체는 채울 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) 메서드에 전달 됩니다. 이 구조는 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) 인터페이스에 포함 된 목록에도 포함 되어 있으며,이는 [enum프레임 정보](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 메서드 호출에서 반환 됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

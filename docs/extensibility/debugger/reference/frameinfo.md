---
title: 프레임인포 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736788"
---
# <a name="frameinfo"></a>FRAMEINFO
스택 프레임에 대해 설명합니다.

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
채워지던 필드를 지정하는 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) 열거형의 플래그 조합입니다.

`m_bstrFuncName`\
스택 프레임과 연결된 함수 이름입니다.

`m_bstrReturnType`\
스택 프레임과 연결된 반환 형식입니다.

`m_bstrArgs`\
스택 프레임과 연결된 함수에 대한 인수입니다.

`m_bstrLanguage`\
함수가 구현되는 언어입니다.

`m_bstrModule`\
스택 프레임과 연결된 모듈 이름입니다.

`m_addrMin`\
최소 물리적 스택 주소입니다.

`m_addrMAX`\
최대 물리적 스택 주소입니다.

`m_pFrame`\
이 스택 프레임을 나타내는 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 개체입니다.

`m_pModule`\
이 스택 프레임을 포함하는 모듈을 나타내는 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 개체입니다.

`m_fHasDebugInfo`\
0이 아닌`TRUE`() 디버그 정보가 지정된 프레임에 있는 경우.

`m_fStaleCode`\
0이 아닌`TRUE`( )( 스택 프레임이 더 이상 유효하지 않은 코드와 연결된 경우)

`m_fAnnotatedFrame`\
0이 아닌`TRUE`경우 () 스택 프레임이 세션 디버그 관리자(SDM)에 의해 추가되는 경우.

## <a name="remarks"></a>설명
이 구조는 채울 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) 메서드에 전달됩니다. 이 구조는 [또한 IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) 인터페이스에 포함 된 목록에 포함 된, 차례로, [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 메서드에 대 한 호출에서 반환 됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

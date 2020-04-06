---
title: DEBUG_REFERENCE_INFO | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e31205f52151679f932877c9c4fdc56907ea59e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737407"
---
# <a name="debug_reference_info"></a>DEBUG_REFERENCE_INFO
참조를 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct tagDEBUG_REFERENCE_INFO {
    DEBUGREF_INFO_FLAGS dwFields;
    BSTR                bstrName;
    BSTR                bstrType;
    BSTR                bstrValue;
    DBG_ATTRIB_FLAGS    dwAttrib;
    REFERENCE_TYPE.     dwRefType;
    IDebugReference2*   m_pReference;
} DEBUG_REFERENCE_INFO;
```

```csharp
public struct DEBUG_REFERENCE_INFO {
    public uint             dwFields;
    public string           bstrName;
    public string           bstrType;
    public string           bstrValue;
    public ulong            dwAttrib;
    public uint.            dwRefType;
    public IDebugReference2 m_pReference;
};
```

## <a name="members"></a>멤버
`dwFields`\
DEBUGREF_INFO_FLAGS 열거형의 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) 플래그 조합으로 채워지어지지 않는 필드를 지정합니다.

`bstrName`\
[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 개체의 사용자 지정 이름입니다.

`bstrType`\
서식이 지정된 문자열로 참조 형식입니다.

`bstrValue`\
서식이 지정된 문자열로 참조 값

`dwAttrib`\
DBG_ATTRIB_FLAGS 열거형의 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) 플래그 조합으로 디버그 속성 속성에 대한 플래그를 지정합니다.

`dwRefType`\
참조 형식이 강한지 약한지 여부를 지정하는 [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) 열거형의 값입니다.

`m_pReference`\
참조 정보를 지정하는 [IDebugReference2 개체입니다.](../../../extensibility/debugger/reference/idebugreference2.md)

## <a name="remarks"></a>설명
이 구조는 채울 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) 메서드에 대 한 호출에 전달 됩니다. 이 구조는 [또한 IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) 인터페이스에서 목록의 일부로 반환 되며, 차례로 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) 메서드에 대 한 호출에서 반환 됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)

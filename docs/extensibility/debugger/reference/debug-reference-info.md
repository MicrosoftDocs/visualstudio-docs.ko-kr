---
title: DEBUG_REFERENCE_INFO | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737407"
---
# <a name="debug_reference_info"></a>DEBUG_REFERENCE_INFO
참조를 설명 합니다.

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
입력 하는 필드를 지정 하는 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) 열거형의 플래그 조합입니다.

`bstrName`\
[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 개체의 사용자 지정 이름입니다.

`bstrType`\
형식이 지정 된 문자열로 된 참조 형식입니다.

`bstrValue`\
형식이 지정 된 문자열로 된 참조 값입니다.

`dwAttrib`\
디버그 속성 특성에 대 한 플래그를 지정 하는 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) 열거형의 플래그 조합입니다.

`dwRefType`\
참조 형식이 강력 하거나 weak 인지 여부를 지정 하는 [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) 열거형의 값입니다.

`m_pReference`\
참조 정보를 지정 하는 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 개체입니다.

## <a name="remarks"></a>설명
이 구조체는 채워질 [Getreferenceinfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) 메서드에 대 한 호출에 전달 됩니다. 이 구조체는 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) 인터페이스에서 목록의 일부로도 반환 됩니다 .이는 차례로 [enumchildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) 메서드 호출에서 반환 됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)

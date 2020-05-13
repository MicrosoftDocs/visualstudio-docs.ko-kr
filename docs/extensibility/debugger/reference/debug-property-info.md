---
title: DEBUG_PROPERTY_INFO | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34fc1b5103949a767a3ee448618cbb708ea6a48b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737455"
---
# <a name="debug_property_info"></a>DEBUG_PROPERTY_INFO
디버그 속성에 대한 정보를 포함합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct tagDEBUG_PROPERTY_INFO {
    DEBUGPROP_INFO_FLAGS dwValidFields;
    BSTR                 bstrFullName;
    BSTR                 bstrName;
    BSTR                 bstrType;
    BSTR                 bstrValue;
    IDebugProperty2*     pProperty;
    DBG_ATTRIB_FLAGS     dwAttrib;
} DEBUG_PROPERTY_INFO;
```

```csharp
public struct DEBUG_PROPERTY_INFO {
    public uint            dwValidFields;
    public string          bstrFullName;
    public string          bstrName;
    public string          bstrType;
    public string          bstrValue;
    public IDebugProperty2 pProperty;
    public ulong           dwAttrib;
};
```

## <a name="members"></a>멤버
`dwValidFields`\
[채워지던](../../../extensibility/debugger/reference/debugprop-info-flags.md) 필드를 지정하는 DEBUGPROP_INFO_FLAGS 열거형의 플래그 조합입니다.

`bstrFullName`\
속성의 전체 이름입니다.

`bstrName`\
컨텍스트 내의 속성 이름입니다.

`bstrType`\
형식이 지정된 문자열로 속성 형식을 지정합니다.

`bstrValue`\
형식이 지정된 문자열로 속성 값입니다.

`pProperty`\
이 구조에서 설명하는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 개체입니다.

`dwAttrib`\
이 속성의 특성을 설명하는 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) 열거형의 플래그 조합입니다.

## <a name="remarks"></a>설명
속성은 이름, 형식 및 값을 포함하는 계층적 특성의 개체입니다. 예를 들어 속성은 지역 변수, 매개 변수, 감시 변수 및 식 및 레지스터를 설명할 수 있습니다.

이 구조는 채워진 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 메서드에 전달됩니다. 이 구조는 [또한 IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 인터페이스에서 이 구조의 목록의 일부로 반환되며, 이 인터페이스는 [차례로 EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 및 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) 메서드에 대한 호출에서 반환됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [겟프로퍼정보](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)

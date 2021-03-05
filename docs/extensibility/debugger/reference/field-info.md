---
description: 이 구조는 지역 변수, 매개 변수 또는 기타 필드를 설명 합니다.
title: FIELD_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 47b7c7cb3a77d0ad925b044130901dd481b99943
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162435"
---
# <a name="field_info"></a>FIELD_INFO
이 구조는 지역 변수, 매개 변수 또는 기타 필드를 설명 합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _tagFieldInfo {
    FIELD_INFO_FIELDS dwFields;
    BSTR              bstrFullName;
    BSTR              bstrName;
    BSTR              bstrType;
    FIELD_MODIFIERS   dwModifiers;
} FIELD_INFO;
```

```csharp
public struct FIELD_INFO {
    public uint   dwFields;
    public string bstrFullName;
    public string bstrName;
    public string bstrType;
    public uint   dwModifiers;
};
```

## <a name="members"></a>멤버
`dwFields`\
채워질 멤버를 지정 하는 [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) 열거형의 플래그 조합입니다.

`bstrFullName`\
필드의 전체 이름입니다.

`bstrName`\
필드의 약식 이름입니다.

`bstrType`\
필드의 형식입니다.

`dwModifiers`\
필드를 설명 하는 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) 열거형의 플래그 조합입니다.

## <a name="remarks"></a>설명
이 구조는 입력 된 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) 메서드에 전달 됩니다.

## <a name="requirements"></a>요구 사항
헤더: sh

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)

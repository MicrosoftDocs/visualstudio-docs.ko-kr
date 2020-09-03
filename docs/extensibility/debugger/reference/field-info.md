---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e2089746adecc583d04176afca18ad19826ea53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736889"
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

## <a name="see-also"></a>추가 정보
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)

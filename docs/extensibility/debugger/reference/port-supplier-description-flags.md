---
title: PORT_SUPPLIER_DESCRIPTION_FLAGS | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- PORT_SUPPLIER_DESCRIPTION_FLAGS enumeration
ms.assetid: 5acee0ee-3a20-41c9-a7dc-0dadae6a5ba5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 26022098eb4233186a1442bde38fe4325accfdd1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713986"
---
# <a name="port_supplier_description_flags"></a>PORT_SUPPLIER_DESCRIPTION_FLAGS

포트 공급자에 대해 검색할 수 있는 메타데이터를 정의합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_PORT_SUPPLIER_DESCRIPTION_FLAGS
{
    PSDFLAG_SHOW_WARNING_ICON = 0x1
};
typedef DWORD PORT_SUPPLIER_DESCRIPTION_FLAGS;
```

```csharp
public enum enum_PORT_SUPPLIER_DESCRIPTION_FLAGS
{
    PSDFLAG_SHOW_WARNING_ICON = 0x1
};
```

## <a name="fields"></a>필드

`PSDFLAG_SHOW_WARNING_ICON`\
이 옵션을 선택하면 경고 아이콘이 UI에 표시됩니다.

## <a name="remarks"></a>설명

이 열거형은 [GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md) 메서드에 의해 반환됩니다.

## <a name="requirements"></a>요구 사항

헤더: Msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조

- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [설명 받기](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)

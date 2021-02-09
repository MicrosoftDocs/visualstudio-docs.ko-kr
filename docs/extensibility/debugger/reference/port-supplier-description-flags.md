---
title: PORT_SUPPLIER_DESCRIPTION_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- PORT_SUPPLIER_DESCRIPTION_FLAGS enumeration
ms.assetid: 5acee0ee-3a20-41c9-a7dc-0dadae6a5ba5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2fd9e9f5e6cdb8f56e16622cc05debf69c8c7f3d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889969"
---
# <a name="port_supplier_description_flags"></a>PORT_SUPPLIER_DESCRIPTION_FLAGS

포트 공급자에 대해 검색할 수 있는 메타 데이터를 정의 합니다.

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
이 확인란이 선택 되어 있으면 UI에 경고 아이콘이 표시 됩니다.

## <a name="remarks"></a>설명

이 열거형은 [Getdescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md) 메서드에 의해 반환 됩니다.

## <a name="requirements"></a>요구 사항

헤더: Msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조

- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)

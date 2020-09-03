---
title: DEBUG_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe778ba3ed80930a4cd7b4fa1170f286b3ccf6ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737514"
---
# <a name="debug_address"></a>DEBUG_ADDRESS
이 구조는 주소를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _tagDEBUG_ADDRESS {
    ULONG32             ulAppDomainID;
    GUID                guidModule;
    _mdToken            tokClass;
    DEBUG_ADDRESS_UNION addr;
} DEBUG_ADDRESS;
```

```csharp
public struct DEBUG_ADDRESS {
    public uint                ulAppDomainID;
    public Guid                guidModule;
    public int                 tokClass;
    public DEBUG_ADDRESS_UNION addr;
}
```

## <a name="members"></a>멤버
`ulAppDomainID`\
프로세스 ID입니다.

`guidModule`\
이 주소를 포함 하는 모듈의 GUID입니다.

`tokClass`\
이 주소의 클래스 또는 형식을 식별 하는 토큰입니다.

> [!NOTE]
> 이 값은 기호 공급자에만 해당 되므로 클래스 형식에 대 한 식별자가 아닌 일반적인 의미는 없습니다.

`addr`\
개별 주소 유형을 설명 하는 구조체의 합집합을 포함 하는 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) 구조체입니다. 값 `addr` 입니다.`dwKind` 는 union을 해석 하는 방법을 설명 하는 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) 열거형에서 제공 됩니다.

## <a name="remarks"></a>설명
이 구조체는 채워질 [Getaddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) 메서드에 전달 됩니다.

**경고 [c + + 전용]**

`addr.dwKind`가이 `ADDRESS_KIND_METADATA_LOCAL` 고 `addr.addr.addrLocal.pLocal` 가 null 값이 아니면 토큰 포인터에서를 호출 해야 합니다 `Release` .

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>요구 사항
헤더: sh

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)

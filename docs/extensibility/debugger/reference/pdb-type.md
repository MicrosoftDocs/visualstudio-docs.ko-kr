---
title: PDB_TYPE | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f736d7d9b190fc46945e2f4f7c309b88c3e851f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714100"
---
# <a name="pdb_type"></a>PDB_TYPE

이 구조는 PDB 기호에서 가져온 필드 유형에 대한 정보를 지정합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _tagTYPE_PDB {
    ULONG32 ulAppDomainID;
    GUID    guidModule;
    DWORD   symid;
} PDB_TYPE;
```

```csharp
public struct PDB_TYPE {
    public uint ulAppDomainID;
    public Guid guidModule;
    public uint symid;
};
```

## <a name="members"></a>멤버

`ulAppDomainID`\
기호가 온 응용 프로그램의 ID입니다. 이는 응용 프로그램의 인스턴스를 고유하게 식별하는 데 사용됩니다.

`guidModule`\
이 필드를 포함하는 모듈의 GUID입니다.

`symid`\
이 필드에 해당하는 기호의 ID입니다.

## <a name="remarks"></a>설명

이 구조는 `dwKind` `TYPE_INFO` 구조의 필드가 설정될 때 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) 구조체에서 `TYPE_KIND_PDB` 연합의 일부로 [나타납니다(dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) 열거된 값).

## <a name="requirements"></a>요구 사항

헤더: sh.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조

- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)

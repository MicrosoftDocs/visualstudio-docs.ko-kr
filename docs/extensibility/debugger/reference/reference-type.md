---
title: REFERENCE_TYPE | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- REFERENCE_TYPE
helpviewer_keywords:
- REFERENCE_TYPE enumeration
ms.assetid: b1ffba10-eb9d-48ba-bf48-6d8b71d6f270
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29ce6ad17aa32b98fd28914c422a49bd8bcc14b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713667"
---
# <a name="reference_type"></a>REFERENCE_TYPE
참조 유형을 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_REFERENCE_TYPE { 
   REF_TYPE_WEAK   = 0x0001,
   REF_TYPE_STRONG = 0x0002
};
typedef DWORD REFERENCE_TYPE;
```

```csharp
public enum enum_REFERENCE_TYPE { 
   REF_TYPE_WEAK   = 0x0001,
   REF_TYPE_STRONG = 0x0002
};
```

## <a name="fields"></a>필드
 `REF_TYPE_WEAK`\
 약한 참조를 지정합니다. 을 함께 `REF_TYPE_STRONG`사용할 수 없습니다.

 `REF_TYPE_STRONG`\
 강력한 참조를 지정합니다. 을 함께 `REF_TYPE_WEAK`사용할 수 없습니다.

## <a name="remarks"></a>설명
 `dwRefType` [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 구조의 부재로 사용됩니다.

 [SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md) 메서드에 매개 변수로 전달 되었습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)

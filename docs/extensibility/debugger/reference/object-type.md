---
title: OBJECT_TYPE | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4ffb85a14e42dd57c345481285eb1f776b3866d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714124"
---
# <a name="object_type"></a>Object_Type
식 계산기에서 개체의 형식을 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_OBJECT_TYPE { 
   OBJECT_TYPE_BOOLEAN = 0x0,
   OBJECT_TYPE_CHAR    = 0x1,
   OBJECT_TYPE_I1      = 0x2,
   OBJECT_TYPE_U1      = 0x3,
   OBJECT_TYPE_I2      = 0x4,
   OBJECT_TYPE_U2      = 0x5,
   OBJECT_TYPE_I4      = 0x6,
   OBJECT_TYPE_U4      = 0x7,
   OBJECT_TYPE_I8      = 0x8,
   OBJECT_TYPE_U8      = 0x9,
   OBJECT_TYPE_R4      = 0xa,
   OBJECT_TYPE_R8      = 0xb,
   OBJECT_TYPE_OBJECT  = 0xc,
   OBJECT_TYPE_NULL    = 0xd,
   OBJECT_TYPE_CLASS   = 0xe
};
typedef DWORD OBJECT_TYPE;
```

```csharp
public enum enum_OBJECT_TYPE { 
   OBJECT_TYPE_BOOLEAN = 0x0,
   OBJECT_TYPE_CHAR    = 0x1,
   OBJECT_TYPE_I1      = 0x2,
   OBJECT_TYPE_U1      = 0x3,
   OBJECT_TYPE_I2      = 0x4,
   OBJECT_TYPE_U2      = 0x5,
   OBJECT_TYPE_I4      = 0x6,
   OBJECT_TYPE_U4      = 0x7,
   OBJECT_TYPE_I8      = 0x8,
   OBJECT_TYPE_U8      = 0x9,
   OBJECT_TYPE_R4      = 0xa,
   OBJECT_TYPE_R8      = 0xb,
   OBJECT_TYPE_OBJECT  = 0xc,
   OBJECT_TYPE_NULL    = 0xd,
   OBJECT_TYPE_CLASS   = 0xe
};
```

## <a name="fields"></a>필드
 `OBJECT_TYPE_BOOLEAN`\
 개체가 부울임을 나타냅니다.

 `OBJECT_TYPE_CHAR`\
 개체가 문자임을 나타냅니다.

 `OBJECT_TYPE_I1`\
 개체가 1바이트 서명된 정수임을 나타냅니다.

 `OBJECT_TYPE_U1`\
 개체가 1바이트 의 부호 없는 정수임을 나타냅니다.

 `OBJECT_TYPE_I2`\
 개체가 2바이트 서명된 정수임을 나타냅니다.

 `OBJECT_TYPE_U2`\
 개체가 2바이트 의 부호 없는 정수임을 나타냅니다.

 `OBJECT_TYPE_I4`\
 개체가 4바이트 서명된 정수임을 나타냅니다.

 `OBJECT_TYPE_U4`\
 개체가 4바이트 의 부호 없는 정수임을 나타냅니다.

 `OBJECT_TYPE_I8`\
 개체가 8바이트 서명된 정수임을 나타냅니다.

 `OBJECT_TYPE_U8`\
 개체가 8바이트 의 서명되지 않은 정수임을 나타냅니다.

 `OBJECT_TYPE_R4`\
 개체가 4바이트 부동 소수점 번호임을 나타냅니다.

 `OBJECT_TYPE_R8`\
 개체가 8바이트 부동 소수점 번호임을 나타냅니다.

 `OBJECT_TYPE_OBJECT`\
 개체가 개체임을 나타냅니다.

 `OBJECT_TYPE_NULL`\
 개체가 NULL임을 나타냅니다.

 `OBJECT_TYPE_CLASS`\
 개체가 클래스임을 나타냅니다.

## <a name="remarks"></a>설명
 [CreatePrimitive개체](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) 및 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) 메서드에 인수로 전달됩니다.

## <a name="requirements"></a>요구 사항
 헤더: ee.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)
- [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)

---
description: 식 계산기에서 개체의 형식을 지정 합니다.
title: OBJECT_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 80ef6cce37967d61611ac48f60aaf5b2a1d184f1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082388"
---
# <a name="object_type"></a>Object_Type
식 계산기에서 개체의 형식을 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_OBJECT_TYPE { 
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
public enum enum_OBJECT_TYPE { 
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
 는 개체가 부울 임을 나타냅니다.

 `OBJECT_TYPE_CHAR`\
 는 개체가 문자 임을 나타냅니다.

 `OBJECT_TYPE_I1`\
 개체가 1 바이트의 부호 있는 정수 임을 나타냅니다.

 `OBJECT_TYPE_U1`\
 개체가 1 바이트 부호 없는 정수 임을 나타냅니다.

 `OBJECT_TYPE_I2`\
 개체가 부호 있는 2 바이트 정수 임을 나타냅니다.

 `OBJECT_TYPE_U2`\
 개체가 부호 없는 2 바이트 정수 임을 나타냅니다.

 `OBJECT_TYPE_I4`\
 개체가 부호 있는 4 바이트 정수 임을 나타냅니다.

 `OBJECT_TYPE_U4`\
 개체가 부호 없는 4 바이트 정수 임을 나타냅니다.

 `OBJECT_TYPE_I8`\
 개체가 8 바이트 부호 있는 정수 임을 나타냅니다.

 `OBJECT_TYPE_U8`\
 개체가 8 바이트의 부호 없는 정수 임을 나타냅니다.

 `OBJECT_TYPE_R4`\
 개체가 4 바이트 부동 소수점 숫자 임을 나타냅니다.

 `OBJECT_TYPE_R8`\
 개체가 8 바이트 부동 소수점 숫자 임을 나타냅니다.

 `OBJECT_TYPE_OBJECT`\
 개체가 개체 임을 나타냅니다.

 `OBJECT_TYPE_NULL`\
 개체가 NULL 임을 나타냅니다.

 `OBJECT_TYPE_CLASS`\
 개체가 클래스 임을 나타냅니다.

## <a name="remarks"></a>설명
 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) 및 [createarrayobject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) 메서드에 인수로 전달 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: ee. h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)
- [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)

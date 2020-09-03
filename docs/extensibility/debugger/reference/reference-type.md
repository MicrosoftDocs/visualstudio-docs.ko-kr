---
title: REFERENCE_TYPE | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713667"
---
# <a name="reference_type"></a>REFERENCE_TYPE
참조 형식을 지정 합니다.

## <a name="syntax"></a>Syntax

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
 약한 참조를 지정 합니다. 는와 함께 사용할 수 없습니다 `REF_TYPE_STRONG` .

 `REF_TYPE_STRONG`\
 강한 참조를 지정 합니다. 는와 함께 사용할 수 없습니다 `REF_TYPE_WEAK` .

## <a name="remarks"></a>설명
 `dwRefType` [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 구조체의 멤버로 사용 됩니다.

 [Setreferencetype](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md) 메서드에 매개 변수로 전달 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)

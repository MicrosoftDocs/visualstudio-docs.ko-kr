---
title: UNMANAGED_ADDRESS_THIS_RELATIVE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE
helpviewer_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE structure
ms.assetid: e6a91ace-2d47-4ff9-aefb-8d8b68eab0b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea493170c7b422129485fcea4248981a2b506001
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713264"
---
# <a name="unmanaged_address_this_relative"></a>UNMANAGED_ADDRESS_THIS_RELATIVE
이 구조체는 `this` Visual Basic의 포인터를 기준으로 하는 주소를 나타냅니다 `Me` .

## <a name="syntax"></a>구문

```cpp
typedef struct _tagUNMANAGED_THIS_RELATIVE {
   DWORD dwOffset;
   DWORD dwBitOffset;
   DWORD dwBitLength;
} UNMANAGED_ADDRESS_THIS_RELATIVE;
```

```csharp
public struct UNMANAGED_THIS_RELATIVE {
   public uint dwOffset;
   public uint dwBitOffset;
   public uint dwBitLength;
}
```

## <a name="members"></a>멤버
 `dwOffset`\
 기본 위치 로부터의 바이트 오프셋입니다 (예: 클래스 vtable의 시작).

 `dwBitOffset`\
 기본 위치에서의 오프셋 (비트 필드를 참조 하지 않는 한 항상 0)입니다.

 `dwBitLength`\
 주소를 나타내는 비트 수입니다 (비트 필드를 참조 하지 않는 한 항상 0).

## <a name="remarks"></a>설명
 이 구조체는 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) `dwKind` 구조체의 필드가 `DEBUG_ADDRESS_UNION` `ADDRESS_KIND_UNMANAGED_THIS_RELATIVE` ( [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) 열거형의 값)로 설정 된 경우 DEBUG_ADDRESS_UNION 구조체의 공용 구조체의 일부입니다.

## <a name="requirements"></a>요구 사항
 헤더: sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)

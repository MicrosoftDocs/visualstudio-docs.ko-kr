---
description: 이 구조체는 메서드 또는 함수의 매개 변수를 나타냅니다.
title: METADATA_ADDRESS_PARAM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_PARAM
helpviewer_keywords:
- METADATA_ADDRESS_PARAM structure
ms.assetid: 90904f19-0e71-4cb3-a56e-6a2e92f66dfc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0171fd59ec034c2015843732cdd361228166e74f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057925"
---
# <a name="metadata_address_param"></a>METADATA_ADDRESS_PARAM
이 구조체는 메서드 또는 함수의 매개 변수를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _tagMETADATA_ADDRESS_PARAM {
   _mdToken tokMethod;
   _mdToken tokParam;
   DWORD    dwIndex;
} METADATA_ADDRESS_PARAM;
```

```csharp
public struct METADATA_ADDRESS_PARAM {
   public int  tokMethod;
   public int  tokParam;
   public uint dwIndex;
}
```

## <a name="members"></a>멤버
 `tokMethod`\
 매개 변수가 포함 된 메서드의 ID입니다.

 `tokParam`\
 매개 변수의 ID입니다.

 `dwIndex`\
 매개 변수 목록에 있는 매개 변수의 인덱스입니다.

## <a name="remarks"></a>설명
 이 구조체는 [](../../../extensibility/debugger/reference/debug-address-union.md) `dwKind` 구조체의 필드가 `DEBUG_ADDRESS_UNION` `ADDRESS_KIND_PARAM` ( [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) 열거형의 값)로 설정 된 경우 DEBUG_ADDRESS_UNION 구조체의 공용 구조체의 일부입니다.

## <a name="requirements"></a>요구 사항
 헤더: sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)

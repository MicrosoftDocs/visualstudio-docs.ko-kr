---
description: 모듈을 설명 하는 데 사용 됩니다.
title: MODULE_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e671b3e578a78665a6a816582e0290119f77ea58
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225476"
---
# <a name="module_flags"></a>MODULE_FLAGS
모듈을 설명 하는 데 사용 됩니다.

## <a name="syntax"></a>구문

```cpp
enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
typedef DWORD MODULE_FLAGS;
```

```csharp
public enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
```

## <a name="fields"></a>필드
 `MODULE_FLAG_NONE`\
 모듈을 지정 하지 않습니다.

 `MODULE_FLAG_SYSTEM`\
 시스템 모듈을 지정 합니다.

 `MODULE_FLAG_SYMBOLS`\
 기호 모듈을 지정 합니다.

 `MODULE_FLAG_64BIT`\
 64 비트 모듈을 지정 합니다.

 `MODULE_FLAG_OPTIMIZED`\
 모듈이 최적화 되었는지 여부를 지정 합니다. 이 상태는 **모듈** 창에 반영 됩니다.

 `MODULE_FLAG_UNOPTIMIZED`\
 모듈이 최적화 되지 않은 것으로 지정 합니다. 이 상태는 **모듈** 창에 반영 됩니다. 이 설정이 기본 상태입니다.

## <a name="remarks"></a>설명
 `m_dwModuleFlags` [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 구조체의 멤버에 사용 됩니다.

 이러한 플래그는 비트와 함께 사용할 수 있습니다 `OR` .

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)

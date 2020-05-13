---
title: MODULE_FLAGS | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78c7f24d64ffca667706c3b2fcebeffad16a9d85
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714264"
---
# <a name="module_flags"></a>MODULE_FLAGS
모듈을 설명하는 데 사용됩니다.

## <a name="syntax"></a>구문

```cpp
enum enum_MODULE_FLAGS { 
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
public enum enum_MODULE_FLAGS { 
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
 모듈을 지정하지 않습니다.

 `MODULE_FLAG_SYSTEM`\
 시스템 모듈을 지정합니다.

 `MODULE_FLAG_SYMBOLS`\
 기호 모듈을 지정합니다.

 `MODULE_FLAG_64BIT`\
 64비트 모듈을 지정합니다.

 `MODULE_FLAG_OPTIMIZED`\
 모듈이 최적화되었음을 지정합니다. 이 상태는 모듈 창에 **반영됩니다.**

 `MODULE_FLAG_UNOPTIMIZED`\
 모듈이 최적화되지 않았다고 지정합니다. 이 상태는 모듈 창에 **반영됩니다.** 이 설정이 기본 상태입니다.

## <a name="remarks"></a>설명
 `m_dwModuleFlags` [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 구조의 부재에 사용됩니다.

 이러한 플래그는 약간 으로 `OR`결합될 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)

---
title: MODULE_INFO_FIELDS | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa64147738a916d44b6924f193860f74bd10a855
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714323"
---
# <a name="module_info_fields"></a>MODULE_INFO_FIELDS
디버그 모듈 정보에 대한 플래그를 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
typedef DWORD MODULE_INFO_FIELDS;
```

```csharp
public enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
```

## <a name="fields"></a>필드
 `MIF_NONE`\
 구조의 필드를 초기화/사용합니다.

 `MIF_NAME`\
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 구조에서 `m_bstrName` 필드를 초기화/사용합니다.

 `MIF_URL`\
 `MODULE_INFO` 구조에서 `m_bstrUrl` 필드를 초기화/사용합니다.

 `MIF_VERSION`\
 `MODULE_INFO` 구조에서 `m_bstrVersion` 필드를 초기화/사용합니다.

 `MIF_DEBUGMESSAGE`\
 `MODULE_INFO` 구조에서 `m_bstrDebugMessage` 필드를 초기화/사용합니다.

 `MIF_LOADADDRESS`\
 `MODULE_INFO` 구조에서 `m_addrLoadAddress` 필드를 초기화/사용합니다.

 `MIF_PREFFEREDADDRESS`\
 `MODULE_INFO` 구조에서 `m_addrPreferredLoadAddress` 필드를 초기화/사용합니다.

 `MIF_SIZE`\
 `MODULE_INFO` 구조에서 `m_dwSize` 필드를 초기화/사용합니다.

 `MIF_LOADORDER`\
 `MODULE_INFO` 구조에서 `m_dwLoadOrder` 필드를 초기화/사용합니다.

 `MIF_TIMESTAMP`\
 `MODULE_INFO` 구조에서 `m_TimeStamp` 필드를 초기화/사용합니다.

 `MIF_URLSYMBOLLOCATION`\
 `MODULE_INFO` 구조에서 `m_bstrUrlSymbolLocation` 필드를 초기화/사용합니다.

 `MIF_FLAGS`\
 `MODULE_INFO` 구조에서 `m_dwModuleFlags` 필드를 초기화/사용합니다.

 `MIF_ALLFIELDS`\
 `MODULE_INFO` 구조의 모든 필드를 초기화/사용합니다.

## <a name="remarks"></a>설명
 이러한 값은 [getInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) 메서드에 인수로 전달되어 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 구조의 필드를 초기화할 수 있는지 나타냅니다.

 이러한 값은 구조에서 `MODULE_INFO` 사용되는 필드와 유효한 필드를 나타내는 데도 사용됩니다.

 이러한 플래그는 약간 으로 `OR`결합될 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)

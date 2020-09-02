---
title: MODULE_INFO_FIELDS | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714323"
---
# <a name="module_info_fields"></a>MODULE_INFO_FIELDS
디버그 모듈 정보에 대 한 플래그를 지정 합니다.

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
 구조에서 필드를 초기화/사용 하지 않습니다.

 `MIF_NAME`\
 `m_bstrName` [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 구조체에서 필드를 초기화/사용 합니다.

 `MIF_URL`\
 `m_bstrUrl`구조에서 필드를 초기화/사용 `MODULE_INFO` 합니다.

 `MIF_VERSION`\
 `m_bstrVersion`구조에서 필드를 초기화/사용 `MODULE_INFO` 합니다.

 `MIF_DEBUGMESSAGE`\
 `m_bstrDebugMessage`구조에서 필드를 초기화/사용 `MODULE_INFO` 합니다.

 `MIF_LOADADDRESS`\
 `m_addrLoadAddress`구조에서 필드를 초기화/사용 `MODULE_INFO` 합니다.

 `MIF_PREFFEREDADDRESS`\
 `m_addrPreferredLoadAddress`구조에서 필드를 초기화/사용 `MODULE_INFO` 합니다.

 `MIF_SIZE`\
 `m_dwSize`구조에서 필드를 초기화/사용 `MODULE_INFO` 합니다.

 `MIF_LOADORDER`\
 `m_dwLoadOrder`구조에서 필드를 초기화/사용 `MODULE_INFO` 합니다.

 `MIF_TIMESTAMP`\
 `m_TimeStamp`구조에서 필드를 초기화/사용 `MODULE_INFO` 합니다.

 `MIF_URLSYMBOLLOCATION`\
 `m_bstrUrlSymbolLocation`구조에서 필드를 초기화/사용 `MODULE_INFO` 합니다.

 `MIF_FLAGS`\
 `m_dwModuleFlags`구조에서 필드를 초기화/사용 `MODULE_INFO` 합니다.

 `MIF_ALLFIELDS`\
 구조체의 모든 필드를 초기화/사용 `MODULE_INFO` 합니다.

## <a name="remarks"></a>설명
 이러한 값은 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) 메서드에 인수로 전달 되어 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 구조체에서 초기화할 필드를 표시 합니다.

 이러한 값은 사용 되는 `MODULE_INFO` 필드와 유효한 필드를 나타내기 위해 구조에도 사용 됩니다.

 이러한 플래그는 비트와 함께 사용할 수 있습니다 `OR` .

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)

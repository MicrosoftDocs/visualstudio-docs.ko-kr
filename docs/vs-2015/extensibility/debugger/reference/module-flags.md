---
title: MODULE_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ae51d604f455b12fd6933a54954b75a97aea4eb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547470"
---
# <a name="module_flags"></a>MODULE_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

모듈을 설명 하는 데 사용 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
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
  
## <a name="members"></a>멤버  
 MODULE_FLAG_NONE  
 모듈을 지정 하지 않습니다.  
  
 MODULE_FLAG_SYSTEM  
 시스템 모듈을 지정 합니다.  
  
 MODULE_FLAG_SYMBOLS  
 기호 모듈을 지정 합니다.  
  
 MODULE_FLAG_64BIT  
 64 비트 모듈을 지정 합니다.  
  
 MODULE_FLAG_OPTIMIZED  
 모듈이 최적화 되었는지 여부를 지정 합니다. 이 상태는 **모듈** 창에 반영 됩니다.  
  
 MODULE_FLAG_UNOPTIMIZED  
 모듈이 최적화 되지 않은 것으로 지정 합니다. 이 상태는 **모듈** 창에 반영 됩니다. 이 설정이 기본 상태입니다.  
  
## <a name="remarks"></a>설명  
 `m_dwModuleFlags` [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 구조체의 멤버에 사용 됩니다.  
  
 이러한 플래그는 비트와 함께 사용할 수 있습니다 `OR` .  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)

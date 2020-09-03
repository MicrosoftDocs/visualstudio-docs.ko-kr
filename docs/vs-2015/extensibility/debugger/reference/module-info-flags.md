---
title: MODULE_INFO_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MODULE_INFO_FLAGS
helpviewer_keywords:
- MODULE_INFO_FLAGS enumeration
ms.assetid: e22d3723-b4d4-4524-8a2f-3adb55bbd273
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 14c9f36c82445f5279615591d38b110163a0829d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181128"
---
# <a name="module_info_flags"></a>MODULE_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

모듈의 기호 상태를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_MODULE_INFO_FLAGS {  
   MIF_SYMBOLS_LOADED = 0x0001  
};  
typedef DWORD MODULE_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_MODULE_INFO_FLAGS {  
   MIF_SYMBOLS_LOADED = 0x0001  
};  
```  
  
## <a name="members"></a>멤버  
 MIF_SYMBOLS_LOADED  
 모듈에서 하나 이상의 기호 집합을 로드 했습니다 (그렇지 않으면 기호가 로드 되지 않음).  
  
## <a name="remarks"></a>설명  
 이 값은 [Get기호 Searchinfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) 메서드에 의해 반환 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)

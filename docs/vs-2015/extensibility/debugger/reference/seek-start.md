---
title: SEEK_START | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 45e664b153c4d643d8fbe8f1cefb207e0a76e18e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204879"
---
# <a name="seek_start"></a>SEEK_START
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

디스어셈블리 스트림에서 검색을 시작할 위치를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
typedef DWORD SEEK_START;  
```  
  
```csharp  
public enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
```  
  
## <a name="members"></a>멤버  
 SEEK_START_BEGIN  
 현재 문서의 시작 부분에서 검색을 시작 합니다.  
  
 SEEK_START_END  
 현재 문서의 끝에서 찾기를 시작 합니다.  
  
 SEEK_START_CURRENT  
 현재 문서의 현재 위치에서 검색을 시작 합니다.  
  
 SEEK_START_CODECONTEXT  
 현재 문서의 지정 된 코드 컨텍스트에서 검색을 시작 합니다.  
  
 SEEK_START_CODELOCID  
 지정 된 코드 위치 식별자에서 찾기를 시작 합니다. 코드 위치 식별자는 [Getcurrentlocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)을 호출 하 여 가져옵니다.  
  
## <a name="remarks"></a>설명  
 [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) 메서드에 인수로 전달 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [찾지](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)   
 [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)

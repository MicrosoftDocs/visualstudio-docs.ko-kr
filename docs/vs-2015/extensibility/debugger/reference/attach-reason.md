---
title: ATTACH_REASON | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c66894fe0515b28037bbb2a19715fa09cbf9fa62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153584"
---
# <a name="attach_reason"></a>ATTACH_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

디버그 엔진 (DE)이 프로그램 노드에 연결 되는 이유를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
typedef DWORD ATTACH_REASON;  
```  
  
```csharp  
public enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
```  
  
## <a name="members"></a>멤버  
 ATTACH_REASON_AUTO  
 프로세스가 현재 디버그 모드에 있기 때문에 연결 합니다.  
  
 ATTACH_REASON_LAUNCH  
 프로세스가 시작 되었으므로 연결 합니다.  
  
 ATTACH_REASON_USER  
 사용자 요청으로 인해 연결 합니다.  
  
## <a name="remarks"></a>설명  
 이러한 값은 [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md) 및 [연결](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) 메서드에 대 한 매개 변수로 사용 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [첨부](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [연결](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)

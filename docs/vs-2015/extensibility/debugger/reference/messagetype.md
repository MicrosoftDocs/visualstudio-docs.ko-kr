---
title: MESSAGETYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c17564c992f4c8855d8a96165975a5d0e132755c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547210"
---
# <a name="messagetype"></a>MESSAGETYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

메시지 유형 및 이유를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```csharp  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## <a name="members"></a>멤버  
 MT_OUTPUTSTRING  
 메시지를 출력 창으로 보내야 함을 나타냅니다. 이는와 함께 사용할 수 없습니다 `MT_MESSAGEBOX` .  
  
 MT_MESSAGEBOX  
 메시지 상자에 메시지를 표시 해야 함을 나타냅니다. 이는와 함께 사용할 수 없습니다 `MT_OUTPUTSTRING` .  
  
 MT_TYPE_MASK  
 메시지의 대상을 격리할 마스크 값입니다.  
  
 MT_REASON_EXCEPTION  
 메시지 상자가 예외의 결과로 표시 됨을 나타냅니다. 이는와 함께 사용할 수 없습니다 `MT_REASON_TRACEPOINT` .  
  
 MT_REASON_TRACEPOINT  
 추적점을 적중 한 결과로 메시지 상자가 표시 됨을 나타냅니다. 이는와 함께 사용할 수 없습니다 `MT_REASON_EXCEPTION` .  
  
 MT_REASON_MASK  
 표시 되는 메시지의 원인을 격리 하는 마스크 값입니다.  
  
## <a name="remarks"></a>설명  
 이러한 값은 [Getmessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) 및 [getmessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) 메서드에서 반환 됩니다.  
  
 이유 값 중 하나를 비트를 사용 하 여 출력 대상 값 중 하나로 결합할 수 있습니다 `OR` .  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)

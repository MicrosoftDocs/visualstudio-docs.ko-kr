---
title: THREADPROPERTIES | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4815a1e42b98fba812e8a3c2a53516bff16081db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204815"
---
# <a name="threadproperties"></a>THREADPROPERTIES
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

스레드의 속성을 설명 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
typedef struct _tagTHREADPROPERTIES {   
   THREADPROPERTY_FIELDS dwFields;  
   DWORD                 dwThreadId;  
   DWORD                 dwSuspendCount;  
   DWORD                 dwThreadState;  
   BSTR                  bstrPriority;  
   BSTR                  bstrName;  
   BSTR                  bstrLocation;  
} THREADPROPERTIES;  
```  
  
```csharp  
public struct THREADPROPERTIES {   
   public uint   dwFields;  
   public uint   dwThreadId;  
   public uint   dwSuspendCount;  
   public uint   dwThreadState;  
   public string bstrPriority;  
   public string bstrName;  
   public string bstrLocation;  
};  
```  
  
## <a name="members"></a>멤버  
 dwFields  
 이 구조체에서 유효한 필드를 설명 하는 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) 열거형의 플래그 조합입니다.  
  
 dwThreadId  
 스레드 ID입니다.  
  
 dwSuspendCount  
 스레드 일시 중단 수입니다.  
  
 dwThreadState  
 운영 스레드의 상태를 나타내는 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) 열거형의 값입니다.  
  
 bstrPriority  
 스레드 우선 순위를 지정 하는 문자열입니다. 예를 들면 "Normal 이상", "Normal" 또는 "Time Critical"입니다.  
  
 bstName  
 스레드 이름입니다.  
  
 bstrLocation  
 일반적으로 실행이 중단 되는 메서드의 이름으로 표현 되는 스레드 위치 (일반적으로 맨 위 스택 프레임)입니다.  
  
## <a name="remarks"></a>설명  
 이 구조체는 [Getthreadproperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) 메서드를 호출 하 여 채워집니다. 반환 되는 정보는 일반적으로 **스레드** 창을 채우는 데 사용 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)

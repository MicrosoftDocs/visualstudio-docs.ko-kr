---
title: AD_PROCESS_ID_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d471a73205383f0f23c5016872712a3ba2c578d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153611"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 구조에서 프로세스 ID를 해석 하는 방법을 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
typedef DWORD AD_PROCESS_ID_TYPE;  
```  
  
```csharp  
public enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
```  
  
## <a name="members"></a>멤버  
 AD_PROCESS_ID_SYSTEM  
 프로세스 ID는 시스템 식별자입니다. `ProcessId.dwProcessId` [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 구조체의 필드를 사용 합니다.  
  
 AD_PROCESS_ID_GUID  
 프로세스 ID는 GUID입니다. `ProcessId.guidProcessId`구조체의 필드를 사용 `AD_PROCESS_ID` 합니다.  
  
## <a name="remarks"></a>설명  
 `ProcessIdType`구조에 포함 된 프로세스 ID의 형식을 식별 하기 위해 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 구조체의 멤버에 사용 됩니다. 구조체의 합집합을 해석 하는 방법을 결정 합니다 `ProcessId` .  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)

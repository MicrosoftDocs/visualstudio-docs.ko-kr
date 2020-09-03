---
title: PROCESS_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9ab05d85b55fd293b648603f067d135f703aff5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205015"
---
# <a name="process_info"></a>PROCESS_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

프로세스에 대 한 정보를 포함 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
typedef struct tagPROCESS_INFO {   
   PROCESS_INFO_FIELDS Fields;  
   BSTR                bstrFileName;  
   BSTR                bstrBaseName;  
   BSTR                bstrTitle;  
   AD_PROCESS_ID       ProcessId;  
   DWORD               dwSessionId;  
   BSTR                bstrAttachedSessionName;  
   FILETIME            CreationTime;  
   PROCESS_INFO_FLAGS  Flags;  
} PROCESS_INFO;  
```  
  
```csharp  
public struct PROCESS_INFO {   
   public uint          Fields;  
   public string        bstrFileName;  
   public string        bstrBaseName;  
   public string        bstrTitle;  
   public AD_PROCESS_ID ProcessId;  
   public uint          dwSessionId;  
   public string        bstrAttachedSessionName;  
   public FILETIME      CreationTime;  
   public uint          Flags;  
};  
```  
  
## <a name="members"></a>멤버  
 필드  
 입력 하는 필드를 지정 하는 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) 열거형의 플래그 조합입니다.  
  
 bstrFileName  
 프로세스의 전체 경로 이름입니다. 매개 변수를 사용 하 여 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) 메서드를 호출 하는 것과 동일 `GN_FILENAME` 합니다.  
  
 bstrBaseName  
 프로세스의 파일 이름 및 확장명입니다. 매개 변수를 사용 하 여 메서드를 호출 하는 것과 동일 `IDebugProcess2::Getname` `GN_BASENAME` 합니다.  
  
 bstrTitle  
 프로세스의 제목입니다 (있는 경우). 매개 변수를 사용 하 여 메서드를 호출 하는 것과 동일 `IDebugProcess2::Getname` `GN_TITLE` 합니다.  
  
 ProcessId  
 프로세스를 식별 하는 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 구조체입니다. [Getphysicalprocessid](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) 메서드를 호출 하는 것과 동일 합니다.  
  
 dwSessionId  
 이 프로세스가 실행 되는 디버그 세션의 식별자입니다.  
  
 bstrAttachedSessionName  
 연결 된 세션 이름입니다. [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) 메서드를 호출 하는 것과 동일 합니다.  
  
 CreationTime  
 프로세스를 만든 시간입니다.  
  
 플래그  
 프로세스의 속성을 지정 하는 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) 열거형의 플래그 조합입니다.  
  
## <a name="remarks"></a>설명  
 이 구조는 입력 된 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) 메서드에 전달 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [Get이상 Processid](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

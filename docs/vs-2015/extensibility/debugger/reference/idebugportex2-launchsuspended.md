---
title: 'IDebugPortEx2:: LaunchSuspended | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3c5e57c003257650f5ca60d4a7c3d9becea3e776
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188449"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

실행 파일을 시작 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT LaunchSuspended(   
   LPCOLESTR        pszExe,  
   LPCOLESTR        pszArgs,  
   LPCOLESTR        pszDir,  
   BSTR             bstrEnv,  
   DWORD            hStdInput,  
   DWORD            hStdOutput,  
   DWORD            hStdError,  
   IDebugProcess2** ppPortProcess  
);  
```  
  
```csharp  
int LaunchSuspended(   
   string             pszExe,  
   string             pszArgs,  
   string             pszDir,  
   string             bstrEnv,  
   uint               hStdInput,  
   uint               hStdOutput,  
   uint               hStdError,  
   out IDebugProcess2 ppPortProcess  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pszExe`  
 진행 시작할 실행 파일의 이름입니다. 이는 전체 경로 이거나 매개 변수에 지정 된 작업 디렉터리에 대 한 상대 경로일 수 있습니다 `pszDir` .  
  
 `pszArgs`  
 진행 실행 파일에 전달할 인수입니다. 인수가 없으면 null 값일 수 있습니다.  
  
 `pszDir`  
 진행 실행 파일에서 사용 하는 작업 디렉터리의 이름입니다. 작업 디렉터리가 필요 하지 않은 경우에는 null 값이 될 수 있습니다.  
  
 `bstrEnv`  
 진행 Null 종료 문자열의 환경 블록, 추가 NULL 종결자가 차례로 표시 됩니다.  
  
 `hStdInput`  
 진행 대체 입력 스트림에 대 한 핸들입니다. 리디렉션이 필요 하지 않으면 0 일 수 있습니다.  
  
 `hStdOutput`  
 진행 대체 출력 스트림에 대 한 핸들입니다. 리디렉션이 필요 하지 않으면 0 일 수 있습니다.  
  
 `hStdError`  
 진행 대체 오류 출력 스트림에 대 한 핸들입니다. 리디렉션이 필요 하지 않으면 0 일 수 있습니다.  
  
 `ppPortProcess`  
 제한이 시작 된 프로세스를 나타내는 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 개체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 코드를 일시 중단 하 고 실행 하지 않도록 프로세스를 시작 해야 합니다. [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) 메서드를 호출 하 여 프로세스를 다시 시작 합니다.  
  
 디버그 엔진에서 프로그램을 시작할 수도 있습니다. 자세한 내용은 [프로그램 시작](../../../extensibility/debugger/launching-a-program.md)을 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [프로그램 시작](../../../extensibility/debugger/launching-a-program.md)

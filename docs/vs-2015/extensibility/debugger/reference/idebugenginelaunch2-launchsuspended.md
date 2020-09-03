---
title: 'IDebugEngineLaunch2:: LaunchSuspended | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08f59f9f099f4cec52760c8a8364feb8f5481ffa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195750"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 메서드는 디버그 엔진 (DE)을 통해 프로세스를 시작 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT LaunchSuspended (   
   LPCOLESTR             pszMachine,  
   IDebugPort2*          pPort,  
   LPCOLESTR             pszExe,  
   LPCOLESTR             pszArgs,  
   LPCOLESTR             pszDir,  
   BSTR                  bstrEnv,  
   LPCOLESTR             pszOptions,  
   LAUNCH_FLAGS          dwLaunchFlags,  
   DWORD                 hStdInput,  
   DWORD                 hStdOutput,  
   DWORD                 hStdError,  
   IDebugEventCallback2* pCallback,  
   IDebugProcess2**      ppDebugProcess  
);  
```  
  
```csharp  
int LaunchSuspended(  
   string               pszServer,   
   IDebugPort2          pPort,   
   string               pszExe,   
   string               pszArgs,   
   string               pszDir,   
   string               bstrEnv,   
   string               pszOptions,   
   enum_LAUNCH_FLAGS    dwLaunchFlags,   
   uint                 hStdInput,   
   uint                 hStdOutput,   
   uint                 hStdError,  
   IDebugEventCallback2 pCallback,   
   out IDebugProcess2   ppProcess  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pszMachine`  
 진행 프로세스를 시작할 컴퓨터의 이름입니다. Null 값을 사용 하 여 로컬 컴퓨터를 지정 합니다.  
  
 `pPort`  
 진행 프로그램이 실행 될 포트를 나타내는 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 인터페이스입니다.  
  
 `pszExe`  
 진행 시작할 실행 파일의 이름입니다.  
  
 `pszArgs`  
 진행 실행 파일에 전달할 인수입니다. 인수가 없으면 null 값일 수 있습니다.  
  
 `pszDir`  
 진행 실행 파일에서 사용 하는 작업 디렉터리의 이름입니다. 작업 디렉터리가 필요 하지 않은 경우에는 null 값이 될 수 있습니다.  
  
 `bstrEnv`  
 진행 NULL 종료 문자열의 환경 블록, 추가 NULL 종결자가 차례로 표시 됩니다.  
  
 `pszOptions`  
 진행 실행 파일에 대 한 옵션입니다.  
  
 `dwLaunchFlags`  
 진행 세션에 대 한 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) 를 지정 합니다.  
  
 `hStdInput`  
 진행 대체 입력 스트림에 대 한 핸들입니다. 리디렉션이 필요 하지 않으면 0 일 수 있습니다.  
  
 `hStdOutput`  
 진행 대체 출력 스트림에 대 한 핸들입니다. 리디렉션이 필요 하지 않으면 0 일 수 있습니다.  
  
 `hStdError`  
 진행 대체 오류 출력 스트림에 대 한 핸들입니다. 리디렉션이 필요 하지 않으면 0 일 수 있습니다.  
  
 `pCallback`  
 진행 디버거 이벤트를 수신 하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 개체입니다.  
  
 `ppDebugProcess`  
 제한이 시작 된 프로세스를 나타내는 결과 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 개체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 일반적으로는 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] [launchsuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) 메서드를 사용 하 여 프로그램을 시작 하 고 디버거를 일시 중단 된 프로그램에 연결 합니다. 그러나 디버그 엔진에서 프로그램을 시작 해야 하는 경우가 있습니다. 예를 들어 디버그 엔진이 인터프리터의 일부이 고 디버깅 중인 프로그램이 해석 된 언어인 경우이 경우에서 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 메서드를 사용 `IDebugEngineLaunch2::LaunchSuspended` 합니다.  
  
 프로세스가 일시 중단 된 상태에서 성공적으로 시작 된 후 프로세스를 시작 하기 위해 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) 메서드가 호출 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended 중단 됨](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)

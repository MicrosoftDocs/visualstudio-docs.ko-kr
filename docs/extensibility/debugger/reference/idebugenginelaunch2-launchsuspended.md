---
title: 아이데버그엔진런칭2::출시 일시 중단 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e802c17d0a93aabbe5c6c0a8573abc6a551944ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730549"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
이 메서드는 DE(디버그 엔진)를 통해 프로세스를 시작합니다.

## <a name="syntax"></a>구문

```cpp
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

## <a name="parameters"></a>매개 변수
`pszMachine`\
【인】 프로세스를 시작할 컴퓨터의 이름입니다. null 값을 사용하여 로컬 컴퓨터를 지정합니다.

`pPort`\
【인】 프로그램이 실행되는 포트를 나타내는 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 인터페이스입니다.

`pszExe`\
【인】 시작할 실행 의 이름입니다.

`pszArgs`\
【인】 실행 할 인수에 전달할 인수입니다. 인수가 없는 경우 null 값일 수 있습니다.

`pszDir`\
【인】 실행 에서 사용되는 작업 디렉터리 이름입니다. 작업 디렉터리를 필요로 하지 않는 경우 null 값이 될 수 있습니다.

`bstrEnv`\
【인】 NULL 종료 된 문자열의 환경 블록 다음에 추가 NULL 종단.

`pszOptions`\
【인】 실행 에 대 한 옵션입니다.

`dwLaunchFlags`\
【인】 세션에 대한 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) 지정합니다.

`hStdInput`\
【인】 대체 입력 스트림을 처리합니다. 리디렉션이 필요하지 않은 경우 0이 될 수 있습니다.

`hStdOutput`\
【인】 대체 출력 스트림을 처리합니다. 리디렉션이 필요하지 않은 경우 0이 될 수 있습니다.

`hStdError`\
【인】 대체 오류 출력 스트림을 처리합니다. 리디렉션이 필요하지 않은 경우 0이 될 수 있습니다.

`pCallback`\
【인】 디버거 이벤트를 수신하는 [IDebugEventCallback2 개체입니다.](../../../extensibility/debugger/reference/idebugeventcallback2.md)

`ppDebugProcess`\
【아웃】 시작된 프로세스를 나타내는 결과 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 일반적으로 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) 메서드를 사용하여 프로그램을 실행한 다음 디버거를 일시 중단된 프로그램에 연결합니다. 그러나 디버그 엔진이 프로그램을 시작해야 하는 상황(예: 디버그 엔진이 인터프리터의 일부이고 디버깅중인 프로그램이 해석된 언어인 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 경우)이 있는 경우 이 메서드를 `IDebugEngineLaunch2::LaunchSuspended` 사용합니다.

 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) 메서드는 프로세스가 일시 중단된 상태에서 성공적으로 시작된 후 프로세스를 시작하도록 호출됩니다.

## <a name="see-also"></a>참조
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)

---
title: 아이디버그포트엑스2::출시 일시 중단 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28ff6065bbe83852b5acc3ffe253a0bdabcc67ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725103"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
실행 파일 파일을 시작합니다.

## <a name="syntax"></a>구문

```cpp
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

## <a name="parameters"></a>매개 변수
`pszExe`\
【인】 시작할 실행 의 이름입니다. 전체 경로이거나 `pszDir` 매개 변수에 지정된 작업 디렉터리와 관련이 있을 수 있습니다.

`pszArgs`\
【인】 실행 할 인수에 전달할 인수입니다. 인수가 없는 경우 null 값일 수 있습니다.

`pszDir`\
【인】 실행 에서 사용되는 작업 디렉터리 이름입니다. 작업 디렉터리를 필요로 하지 않는 경우 null 값이 될 수 있습니다.

`bstrEnv`\
【인】 null 종료 된 문자열의 환경 블록 다음에 추가 NULL 종단.

`hStdInput`\
【인】 대체 입력 스트림을 처리합니다. 리디렉션이 필요하지 않은 경우 0이 될 수 있습니다.

`hStdOutput`\
【인】 대체 출력 스트림을 처리합니다. 리디렉션이 필요하지 않은 경우 0이 될 수 있습니다.

`hStdError`\
【인】 대체 오류 출력 스트림을 처리합니다. 리디렉션이 필요하지 않은 경우 0이 될 수 있습니다.

`ppPortProcess`\
【아웃】 시작된 프로세스를 나타내는 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드는 일시 중단되고 코드를 실행하지 않도록 프로세스를 시작해야 합니다. [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) 메서드를 호출하여 프로세스를 다시 시작합니다.

 디버그 엔진에서 프로그램을 시작할 수도 있습니다. 자세한 내용은 [프로그램 시작](../../../extensibility/debugger/launching-a-program.md)을 참조하십시오.

## <a name="see-also"></a>참조
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [프로그램 시작](../../../extensibility/debugger/launching-a-program.md)

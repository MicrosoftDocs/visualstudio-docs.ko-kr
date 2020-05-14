---
title: IDebugProgram2::GetProcess | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aca1842e92e7e1c164a6468e6c1e94a352ef67c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722786"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
이 프로그램이 실행 중인 프로세스를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetProcess(
   IDebugProcess2** ppProcess
);
```

```csharp
int GetProcess(
   out IDebugProcess2 ppProcess
);
```

## <a name="parameters"></a>매개 변수
`ppProcess`\
【아웃】 프로세스를 나타내는 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 인터페이스를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 DE 버그 엔진 (DE)이 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) 인터페이스를 구현하지 않는 한 DE가 `E_NOTIMPL` 실행 중인 프로세스를 확인할 수 없으므로 이 메서드의 구현을 충족시킬 수 없기 때문에 DE의 구현은 항상 반환되어야 합니다.

 인터페이스를 `IDebugEngineLaunch2` 구현한다는 것은 DE가 프로세스를 만드는 방법을 알고 있어야 함을 의미합니다. 따라서 [DE의 IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스 구현은 어떤 프로세스가 실행되는지 알 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)

---
title: 'IDebugProgram2:: GetProcess | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722786"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
이 프로그램이 실행 되는 프로세스를 가져옵니다.

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
제한이 프로세스를 나타내는 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 인터페이스를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 De (디버그 엔진)가 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) 인터페이스를 구현 하지 않는 한이 메서드의 de 구현은 항상를 반환 해야 합니다 .이 경우 de `E_NOTIMPL` 는 실행 중인 프로세스를 확인할 수 없으므로이 메서드의 구현을 충족 시킬 수 없기 때문입니다.

 인터페이스를 구현 하는 것은 `IDebugEngineLaunch2` de가 프로세스를 만드는 방법을 알고 있어야 한다는 것을 의미 합니다. 따라서 de의 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스 구현은에서 실행 중인 프로세스를 알 수 있습니다.

## <a name="see-also"></a>추가 정보
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)

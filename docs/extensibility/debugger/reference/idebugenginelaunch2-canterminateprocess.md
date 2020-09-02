---
title: 'IDebugEngineLaunch2:: CanTerminateProcess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91c68e0a0e314015c1f2e6df2a96243c6ce854e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730565"
---
# <a name="idebugenginelaunch2canterminateprocess"></a>IDebugEngineLaunch2::CanTerminateProcess
프로세스를 종료할 수 있는지 여부를 확인 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CanTerminateProcess ( 
   IDebugProcess2* pProcess
);
```

```csharp
int CanTerminateProcess ( 
   IDebugProcess2 pProcess
);
```

## <a name="parameters"></a>매개 변수
`pProcess`\
진행 종료할 프로세스를 나타내는 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. 예를 들어 `S_FALSE` 액세스가 거부 되었기 때문에 엔진이 프로세스를 종료할 수 없는 경우를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드가를 반환 하는 경우 `S_OK` [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md) 메서드를 호출 하 여 실제로 프로세스를 종료할 수 있습니다.

## <a name="see-also"></a>추가 정보
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)

---
description: 프로그램에 연결 합니다.
title: 'IDebugProgram2:: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4f9565ea0975e38ced80f0747560cf1a24b4150c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076227"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
프로그램에 연결 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback
);
```

## <a name="parameters"></a>매개 변수
`pCallback`\
진행 디버그 이벤트 알림에 사용할 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. 다음 표에서는 가능한 몇 가지 오류 코드를 보여 줍니다.

|값|Description|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|지정 된 프로그램이 디버거에 이미 연결 되어 있습니다.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|연결 절차를 수행 하는 동안 보안 위반이 발생 했습니다.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|데스크톱 프로그램을 디버거에 연결할 수 없습니다.|

## <a name="remarks"></a>설명
 DE (디버그 엔진)는이 메서드를 호출 하 여 프로그램에 연결 하지 않습니다. 프로그램의 주소 공간에서 DE를 실행 하는 경우 [Onattach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 메서드가 호출 됩니다. 세션 디버그 관리자의 SDM () 주소 공간에서 DE를 실행 하는 경우 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드가 호출 됩니다.

## <a name="see-also"></a>참조
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)

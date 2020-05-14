---
title: IDebugEngine2::D에스트로이프로그램 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce139dd22361d9914693cbe8ad723656ab7d4f26
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731103"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
지정된 프로그램이 비정상적으로 종료되었으며 DE가 프로그램에 대한 모든 참조를 정리하고 프로그램 소멸 이벤트를 보내야 한다는 것을 DE(디버그 엔진)에 알립니다.

## <a name="syntax"></a>구문

```cpp
HRESULT DestroyProgram( 
   IDebugProgram2* pProgram
);
```

```cpp
int DestroyProgram( 
   IDebugProgram2 pProgram
);
```

## <a name="parameters"></a>매개 변수
`pProgram`\
【인】 비정상적으로 종료된 프로그램을 나타내는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 개체입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드가 호출된 후 DE는 [이후에 IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 이벤트를 세션 디버그 관리자(SDM)로 다시 보냅니다.

 DE가 디버깅되는 `E_NOTIMPL`프로그램과 동일한 프로세스에서 실행되는 경우 이 메서드는 구현(반환)되지 않습니다. 이 메서드는 DE가 SDM과 동일한 프로세스에서 실행되는 경우에만 구현됩니다.

## <a name="see-also"></a>참조
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

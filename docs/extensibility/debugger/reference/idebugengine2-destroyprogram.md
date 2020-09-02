---
title: IDebugEngine2::D estroyProgram | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731103"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
지정 된 프로그램이 atypically 종료 되었으며 DE가 프로그램에 대 한 모든 참조를 정리 하 고 프로그램 소멸 이벤트를 전송 해야 함을 디버그 엔진 (DE)에 알립니다.

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
진행 Atypically 종료 된 프로그램을 나타내는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드를 호출한 후 DE는 [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 이벤트를 다시 SDM (세션 디버그 관리자)로 보냅니다.

 `E_NOTIMPL`디버깅이 디버깅 중인 프로그램과 동일한 프로세스에서 실행 되는 경우이 메서드는 구현 되지 않습니다 (반환). 이 메서드는 제거를 SDM과 동일한 프로세스에서 실행 하는 경우에만 구현 됩니다.

## <a name="see-also"></a>추가 정보
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

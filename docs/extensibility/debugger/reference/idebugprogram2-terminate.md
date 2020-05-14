---
title: IDebugProgram2::종료 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 913c90e34e308ce5bb4ceecface739afc8d03f3d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722751"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
프로그램을 종료합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Terminate( 
   void 
);
```

```csharp
int Terminate();
```

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 가능하면 프로그램이 종료되고 프로세스에서 언로드됩니다. 그렇지 않으면 DE(디버그 엔진)가 필요한 정리를 수행합니다.

 이 메서드 또는 [종료](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) 메서드는 일반적으로 모든 디버깅을 중지 하는 사용자에 대 한 응답으로 IDE에 의해 호출 됩니다. 이 메서드의 구현은 이상적으로 프로세스 내에서 프로그램을 종료해야 합니다. 이것이 불가능한 경우 DE는 이 프로세스에서 프로그램이 더 이상 실행되지 않도록 해야 합니다(필요한 정리). 메서드가 `IDebugProcess2::Terminate` IDE에 의해 호출된 경우 `IDebugProgram2::Terminate` 메서드가 호출된 후 전체 프로세스가 언젠가 종료됩니다.

## <a name="see-also"></a>참조
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)

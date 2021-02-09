---
title: 'IDebugProgram2:: Terminate | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74a186bd39dab7ab1f7228504070f50b3aa6c311
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911900"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
프로그램을 종료 합니다.

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
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 가능 하면 프로그램이 종료 되 고 프로세스에서 언로드됩니다. 그렇지 않으면 디버그 엔진 (DE)이 필요한 정리를 수행 합니다.

 이 메서드나 [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) 메서드는 일반적으로 모든 디버깅을 중지 하는 사용자에 대 한 응답으로 IDE에 의해 호출 됩니다. 이 메서드의 구현에서는 프로세스 내에서 프로그램을 종료 하는 것이 가장 좋습니다. 가능 하지 않은 경우에는이 프로세스에서 프로그램이 더 이상 실행 되지 않도록 방지 해야 합니다. `IDebugProcess2::Terminate`IDE에서 메서드를 호출한 경우 메서드가 호출 된 후 전체 프로세스가 종료 됩니다 `IDebugProgram2::Terminate` .

## <a name="see-also"></a>참고 항목
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)

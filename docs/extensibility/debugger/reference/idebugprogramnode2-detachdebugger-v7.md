---
title: IDebugProgramNode2::D에타치디버거_V7 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 925f1b07662ece35d21f9b647681bc898428c4c7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722112"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> 되지 않는. 사용하지 마십시오.

## <a name="syntax"></a>구문

```cpp
HRESULT DetachDebugger_V7 (
   void 
);
```

```csharp
int DetachDebugger_V7 ();
```

## <a name="return-value"></a>Return Value

구현은 항상 `E_NOTIMPL`반환되어야 합니다.

## <a name="remarks"></a>설명

> [!WARNING]
> Visual Studio 2005에서 이 메서드는 더 이상 `E_NOTIMPL`사용되지 않으며 항상 반환해야 합니다.

이 메서드는 디버거가 예기치 않게 종료될 때 호출됩니다. 이 메서드가 호출되면 DE는 사용자가 분리된 것처럼 프로그램을 다시 시작해야 합니다. 더 이상 디버그 이벤트를 전송할 수 없습니다. 프로그램은 디버거의 다른 인스턴스에서 연결할 수 있는 상태여야 합니다.

## <a name="see-also"></a>참조

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

---
title: IDebugProgramNode2::D etachDebugger_V7 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722112"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> Mapi. 사용 하지 마십시오.

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

구현은 항상를 반환 해야 `E_NOTIMPL` 합니다.

## <a name="remarks"></a>설명

> [!WARNING]
> Visual Studio 2005을 사용 하 여이 메서드는 더 이상 사용 되지 않으며 항상를 반환 해야 `E_NOTIMPL` 합니다.

이 메서드는 디버거가 예기치 않게 종료 될 때 호출 됩니다. 이 메서드가 호출 되 면 DE는 사용자가 해당 프로그램에서 분리 된 것 처럼 프로그램을 다시 시작 해야 합니다. 더 이상 디버그 이벤트를 보내지 않습니다. 프로그램은 디버거의 다른 인스턴스에서 연결할 수 있는 상태 여야 합니다.

## <a name="see-also"></a>추가 정보

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

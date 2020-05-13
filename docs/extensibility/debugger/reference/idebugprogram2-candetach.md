---
title: IDebugProgram2::캔데타흐 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3d03d942bbc052a7ac6bebc6a89c55ec21a1b4c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723128"
---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
DEBug 엔진(DE)이 프로그램에서 분리될 수 있는지 확인합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CanDetach(
   void
);
```

```csharp
int CanDetach();
```

## <a name="return-value"></a>Return Value
 분리할 수 있는 `S_OK`경우 반환합니다. 그렇지 않으면 오류 코드를 반환합니다. DE가 프로그램에서 분리할 수 없는 경우 반환합니다. `S_FALSE`

## <a name="see-also"></a>참조
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

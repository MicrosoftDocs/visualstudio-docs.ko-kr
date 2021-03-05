---
description: 프로그램의 종료 코드를 가져옵니다.
title: 'IDebugProgramDestroyEvent2:: GetExitCode | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramDestroyEvent2::GetExitCode
helpviewer_keywords:
- IDebugProgramDestroyEvent2::GetExitCode
ms.assetid: 7f540cf6-e2d1-42b0-913e-a26d654b7659
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bf8ba64de9d0065c174c3592f0431e2901a4d1e0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151599"
---
# <a name="idebugprogramdestroyevent2getexitcode"></a>IDebugProgramDestroyEvent2::GetExitCode
프로그램의 종료 코드를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetExitCode( 
   DWORD* pdwExit
);
```

```csharp
int GetExitCode( 
   out uint pdwExit
);
```

## <a name="parameters"></a>매개 변수
`pdwExit`\
제한이 프로그램의 종료 코드를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

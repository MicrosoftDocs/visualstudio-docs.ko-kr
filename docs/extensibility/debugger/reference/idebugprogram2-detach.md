---
description: 프로그램에서 디버그 엔진을 분리 합니다.
title: IDebugProgram2::D etach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Detach
helpviewer_keywords:
- IDebugProgram2::Detach
ms.assetid: 5e8d88b0-a8d4-4746-88c0-ad332ee73f33
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d303db7043865d770604d7feeec57ddf584fc346
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146173"
---
# <a name="idebugprogram2detach"></a>IDebugProgram2::Detach
프로그램에서 디버그 엔진을 분리 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Detach( 
   void 
);
```

```csharp
int Detach();
```

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 분리 된 프로그램은 계속 실행 되지만 더 이상 디버그 세션의 일부가 아닙니다. 디버그 엔진이 분리 된 후에는 더 이상 프로그램 디버그 이벤트가 전송 되지 않습니다.

## <a name="see-also"></a>참고 항목
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

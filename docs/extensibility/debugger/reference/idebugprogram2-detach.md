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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e9e7527ee13c703bbf7e1ba5a15ae225cf87c0b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076097"
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

## <a name="see-also"></a>참조
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

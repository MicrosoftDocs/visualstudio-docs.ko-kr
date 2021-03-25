---
description: 디버그 엔진 (DE)이 프로그램에서 분리 될 수 있는지 여부를 확인 합니다.
title: 'IDebugProgram2:: CanDetach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e751429fe26060a515f94aa3d402954ff598d39
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076175"
---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
디버그 엔진 (DE)이 프로그램에서 분리 될 수 있는지 여부를 확인 합니다.

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
 가 분리 될 수 있는 경우는를 반환 하 `S_OK` 고, 그렇지 않으면 오류 코드를 반환 합니다. `S_FALSE`DE가 프로그램에서 분리 될 수 없으면를 반환 합니다.

## <a name="see-also"></a>참조
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

---
description: 프로그램 열거형을 첫 번째 요소로 다시 설정 합니다.
title: 'IEnumDebugPrograms2:: Reset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Reset
helpviewer_keywords:
- IEnumDebugPrograms2::Reset
ms.assetid: b289242b-24ea-4df3-a811-20b0c8a903d6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a54961b40f4bde286d2adfd0b8bb791a9750583e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079958"
---
# <a name="ienumdebugprograms2reset"></a>IEnumDebugPrograms2::Reset
열거형을 첫 번째 요소로 다시 설정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드가 호출 된 후 [다음](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md) 메서드에 대 한 다음 호출에서 열거형의 첫 번째 요소를 반환 합니다.

## <a name="see-also"></a>참조
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)

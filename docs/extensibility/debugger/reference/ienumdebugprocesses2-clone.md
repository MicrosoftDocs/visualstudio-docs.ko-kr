---
description: 현재 프로세스 열거형의 복사본을 별도의 개체로 반환 합니다.
title: 'IEnumDebugProcesses2:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2::Clone
helpviewer_keywords:
- IEnumDebugProcesses2::Clone
ms.assetid: 3d4196d3-5a80-4f76-b8b2-f72e80c8d406
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 964aa8d280ec5d3a2803c88ea40284ed6d10110b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058120"
---
# <a name="ienumdebugprocesses2clone"></a>IEnumDebugProcesses2::Clone
현재 열거형의 복사본을 별도의 개체로 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Clone(
   IEnumDebugProcesses2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugProcesses2 ppEnum
);
```

## <a name="parameters"></a>매개 변수
`ppEnum`\
제한이 이 열거형의 복사본을 별도의 개체로 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 열거형의 복사본은이 메서드가 호출 될 때의 원래 상태와 동일 합니다. 그러나 복사본과 원래 상태는 별개 이며 개별적으로 변경할 수 있습니다.

## <a name="see-also"></a>참조
- [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)

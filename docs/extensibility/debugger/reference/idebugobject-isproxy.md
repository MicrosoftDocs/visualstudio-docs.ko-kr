---
description: 개체가 투명 프록시 인지 여부를 확인 합니다.
title: 'IDebugObject:: IsProxy | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugObject::IsProxy
- IsProxy
ms.assetid: 06c66b87-db95-4400-ab26-5d33e743a439
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f66c8f460e284776f15e393a4adbc8bfd0ea9076
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054142"
---
# <a name="idebugobjectisproxy"></a>IDebugObject::IsProxy
개체가 투명 프록시 인지 여부를 확인 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT IsProxy (
   BOOL* pfIsProxy
);
```

```csharp
int IsProxy (
   out bool pfIsProxy
);
```

## <a name="parameters"></a>매개 변수
`pfIsProxy`\
[out] `TRUE` 개체가 투명 프록시 이면이 고, 그렇지 않으면입니다. 그렇지 않으면 `FALSE` 입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 기본 c + + 디버그 엔진에 의해 구현 됩니다.

## <a name="see-also"></a>참조
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

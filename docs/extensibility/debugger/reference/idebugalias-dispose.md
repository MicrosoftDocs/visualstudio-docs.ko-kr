---
description: 이 별칭을 제거 하도록 표시 합니다.
title: IDebugAlias::D ispose | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::Dispose
helpviewer_keywords:
- IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7428b1a8d0dcb95d14274270542d4bba8c50bde9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059174"
---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
이 별칭을 제거 하도록 표시 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Dispose();
```

```csharp
int Dispose();
```

## <a name="parameters"></a>매개 변수
 없음

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드를 호출 하면 별칭을 더 이상 사용할 수 없습니다.

## <a name="see-also"></a>참조
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)

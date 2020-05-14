---
title: IDebugDefaultPort2::쿼리로컬 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c06230f7bbd1825fe73a22f9b1fdc35aea35c499
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732331"
---
# <a name="idebugdefaultport2queryislocal"></a>IDebugDefaultPort2::QueryIsLocal
이 메서드는 이 포트가 로컬 컴퓨터에 있는지 여부를 결정합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT QueryIsLocal(
   void
);
```

```csharp
int QueryIsLocal();
```

## <a name="return-value"></a>Return Value
 이 `S_OK` 포트가 로컬(호출자와 동일한 컴퓨터에서) `S_FALSE` 또는 포트가 다른 컴퓨터에 있는 경우 반환됩니다.

## <a name="see-also"></a>참조
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)

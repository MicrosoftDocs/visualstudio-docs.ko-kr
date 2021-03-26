---
description: 이 메서드는이 포트가 로컬 컴퓨터에 있는지 여부를 확인 합니다.
title: 'IDebugDefaultPort2:: QueryIsLocal | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e678e1219bfc9c64fe33be545e82e7fbb596b2db
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067129"
---
# <a name="idebugdefaultport2queryislocal"></a>IDebugDefaultPort2::QueryIsLocal
이 메서드는이 포트가 로컬 컴퓨터에 있는지 여부를 확인 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT QueryIsLocal(
   void
);
```

```csharp
int QueryIsLocal();
```

## <a name="return-value"></a>Return Value
 `S_OK`이 포트가 호출자와 같은 컴퓨터에 있는 로컬 이거나 `S_FALSE` 포트가 다른 컴퓨터에 있는 경우를 반환 합니다.

## <a name="see-also"></a>참조
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)

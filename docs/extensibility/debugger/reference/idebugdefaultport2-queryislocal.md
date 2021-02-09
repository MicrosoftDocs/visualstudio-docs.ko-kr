---
title: 'IDebugDefaultPort2:: QueryIsLocal | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2a4c4f5d8e9810f0828ac5ffb85173ef9ed77626
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896229"
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

## <a name="see-also"></a>참고 항목
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)

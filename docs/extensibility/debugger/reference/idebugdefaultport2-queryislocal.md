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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c06230f7bbd1825fe73a22f9b1fdc35aea35c499
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732331"
---
# <a name="idebugdefaultport2queryislocal"></a>IDebugDefaultPort2::QueryIsLocal
이 메서드는이 포트가 로컬 컴퓨터에 있는지 여부를 확인 합니다.

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
 `S_OK`이 포트가 호출자와 같은 컴퓨터에 있는 로컬 이거나 `S_FALSE` 포트가 다른 컴퓨터에 있는 경우를 반환 합니다.

## <a name="see-also"></a>추가 정보
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)

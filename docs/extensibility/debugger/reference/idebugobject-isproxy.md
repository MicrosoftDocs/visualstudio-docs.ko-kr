---
title: 'IDebugObject:: IsProxy | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugObject::IsProxy
- IsProxy
ms.assetid: 06c66b87-db95-4400-ab26-5d33e743a439
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 216d1e0e007376b88b8befd2bf654a65192b13c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953645"
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

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 기본 c + + 디버그 엔진에 의해 구현 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

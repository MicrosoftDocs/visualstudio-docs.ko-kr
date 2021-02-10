---
title: 'IDebugObject:: IsReadOnly | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4e7d27e6a437c46d2ee72eb4fd5f79eaa9e912ac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953632"
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
이 개체가 읽기 전용인 지 여부를 확인 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT IsReadOnly( 
   BOOL* pfIsReadOnly
);
```

```csharp
int IsReadOnly(
   out int pfIsReadOnly
);
```

## <a name="parameters"></a>매개 변수
`pfIsReadOnly`\
제한이 `TRUE`이 개체가 읽기 전용 이면 0이 아닌 값을 반환 하 고, 그렇지 않으면 0 ()을 반환 `FALSE` 합니다.

## <a name="return-value"></a>Return Value
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 읽기 전용 개체를 만든 후에는 해당 값을 변경할 수 없습니다.

## <a name="see-also"></a>참고 항목
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

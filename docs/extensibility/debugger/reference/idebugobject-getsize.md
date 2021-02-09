---
title: 'IDebugObject:: GetSize | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetSize
helpviewer_keywords:
- IDebugObject::GetSize method
ms.assetid: 89af423b-36eb-479d-b2de-2693455eca15
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a475b4d6d9b0af8b4c55a3d949fdc4ed172aa337
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846831"
---
# <a name="idebugobjectgetsize"></a>IDebugObject::GetSize
개체의 크기 (바이트)를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetSize( 
   UINT* pnSize
);
```

```csharp
int GetSize(
   out uint pnSize
);
```

## <a name="parameters"></a>매개 변수
`pnSize`\
제한이 크기 (바이트)를 반환 합니다.

## <a name="return-value"></a>Return Value
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md) 메서드를 사용 하 여 값을 바이트 시퀀스로 검색 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)

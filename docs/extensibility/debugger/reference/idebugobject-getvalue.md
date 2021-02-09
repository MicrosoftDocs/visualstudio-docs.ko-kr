---
title: 'IDebugObject:: GetValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7534a05879bdae0a885ae0cbe23d072c30132d0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846805"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
개체의 값을 연속 된 일련의 바이트로 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int GetValue(
   ref byte[] pValue,
   uint nSize
);
```

## <a name="parameters"></a>매개 변수
`pValue`\
[in, out] 개체의 값을 나타내는 연속 된 일련의 바이트로 채워진 배열입니다.

`nSize`\
진행 인출할 최대 바이트 수입니다.

## <a name="return-value"></a>Return Value
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 [Getsize](../../../extensibility/debugger/reference/idebugobject-getsize.md) 메서드를 호출 하 여 페치할 수 있는 총 값 바이트 수를 가져옵니다.

## <a name="see-also"></a>참고 항목
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

---
description: 개체의 값을 연속 된 일련의 바이트로 가져옵니다.
title: 'IDebugObject:: GetValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d957743a725ad462a9ed95fca6ebdffbecb6de16
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054129"
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

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 [Getsize](../../../extensibility/debugger/reference/idebugobject-getsize.md) 메서드를 호출 하 여 페치할 수 있는 총 값 바이트 수를 가져옵니다.

## <a name="see-also"></a>참조
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

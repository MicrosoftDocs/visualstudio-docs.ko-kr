---
title: 아이디버그 오브젝트::겟밸류 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45d555cbea6bf8239ef4527ba982072e17532af4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726549"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
개체값을 연속적인 바이트 로 가져옵니다.

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
【인, 아웃】 개체의 값을 나타내는 연속된 바이트 시리즈로 채워진 배열입니다.

`nSize`\
【인】 가져올 최대 바이트 수입니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) 메서드를 호출하여 가져올 수 있는 총 값 바이트 수를 가져옵니다.

## <a name="see-also"></a>참조
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

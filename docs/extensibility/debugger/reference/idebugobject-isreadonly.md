---
title: 아이디버그 오브젝트::이읽기전용 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 19546550f916e9d42adf634b0d85958ce9697d28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726417"
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
이 개체가 읽기 전용인지 확인합니다.

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
【아웃】 이 개체가`TRUE`읽기 전용인 경우 0이 아닌 () 반환합니다. 그렇지 않으면 0`FALSE`()을 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 읽기 전용 개체는 생성된 후에 해당 값을 변경할 수 없습니다.

## <a name="see-also"></a>참조
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

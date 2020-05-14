---
title: 아이디버그모듈3:이유저코드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 435ec50ef5437e5aca5d3722a2041115882d15f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726835"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
모듈이 사용자 코드를 나타내는지 여부에 대한 정보를 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT IsUserCode(
   BOOL* pfUser
);
```

```csharp
int IsUserCode(
   out int pfUser
);
```

## <a name="parameters"></a>매개 변수
`pfUser`\
【아웃】 비제로`TRUE`() 모듈이 사용자 코드를`FALSE`나타내는 경우, 0 () 그렇지 않은 경우.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)

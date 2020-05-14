---
title: 아이디버그오브젝트2::이유저데이터 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce4a7035ac3786f0cc1644e2ebbb0c142167e2b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726096"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
개체가 사용자 데이터를 나타내는지 여부를 결정합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT IsUserData(
   BOOL* pfUser
);
```

```csharp
int IsUserData(
   out int pfUser
);
```

## <a name="parameters"></a>매개 변수
`pfUser`\
【아웃】 개체가 사용자`TRUE`데이터를 나타내는 경우 비영 () 반환합니다. 0`FALSE`() 하지 않는 경우.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 사용자 데이터는 JustMyCode로 지정된 모듈의 일부인 모든 개체입니다(모듈을 사용자 코드로 표시하여 스택 추적에 표시되는 사용자 구성 옵션).

## <a name="see-also"></a>참조
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)

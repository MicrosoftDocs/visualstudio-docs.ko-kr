---
title: 아이디버그오브젝트2:이센크나디드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a90ff97b87ec2abaab87dfece5b2a2ac1cabb28c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726107"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
이 메서드는 이 개체 또는 상위 컨테이너의 편집 및 계속 상태가 최신 상태가 아닙니다. 사용자 지정 식 계산기는 이 메서드를 구현하지 않으며 항상 을 반환합니다. `E_NOTIMPL`

## <a name="syntax"></a>구문

```cpp
HRESULT IsEncOutdated(
   BOOL* pfEncOutdated
);
```

```csharp
int IsEncOutdated(
   out int pfEncOutdated
);
```

## <a name="parameters"></a>매개 변수
`pfEncOutdated`\
【아웃】 Nonzero`TRUE`() 편집 및 계속 상태가 오래된 경우`FALSE`0 () 이 아닌 경우.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

> [!NOTE]
> 사용자 지정 식 계산기는 항상 을 반환해야 `E_NOTIMPL`합니다.

## <a name="see-also"></a>참조
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)

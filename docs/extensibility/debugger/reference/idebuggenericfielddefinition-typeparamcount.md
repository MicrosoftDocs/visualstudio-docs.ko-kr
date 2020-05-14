---
title: 아이데버그제네릭필드정의::타입파라엠카운트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TypeParamCount
- IDebugGenericFieldDefinition::TypeParamCount
ms.assetid: d41dd5ea-aa25-4bf3-bcfd-e0bf451ead49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a488bce2ad5822f875776bdfc4c4de29eee71bbb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728230"
---
# <a name="idebuggenericfielddefinitiontypeparamcount"></a>IDebugGenericFieldDefinition::TypeParamCount
제네릭 필드와 연결된 형식 매개 변수의 수를 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT TypeParamCount(
   ULONG32* pcParams
);
```

```csharp
int TypeParamCount(
   ref uint pcParams
);
```

## <a name="parameters"></a>매개 변수
`pcParams`\
【인, 아웃】 형식 매개 변수의 수입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 목록\<T가> 경우 이 메서드는\<1을 반환하고 목록 T1,T2> 경우 이 메서드는 2를 반환합니다. 이 메서드는 형식 매개 변수가 없는 경우 0을 반환합니다.

## <a name="see-also"></a>참조
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)

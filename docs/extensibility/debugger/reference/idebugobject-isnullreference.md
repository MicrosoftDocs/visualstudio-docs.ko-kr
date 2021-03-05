---
description: 이 개체가 null 참조 인지 여부를 테스트 합니다.
title: 'IDebugObject:: IsNullReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 844e6c92385c1aa719d3c9d0ff399db9104dccc0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161513"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
이 개체가 null 참조 인지 여부를 테스트 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT IsNullReference( 
   BOOL* pfIsNull
);
```

```csharp
int IsNullReference(
   out int pfIsNull
);
```

## <a name="parameters"></a>매개 변수
`pfIsNull`\
제한이 `TRUE`이 개체가 null 참조 이면 0이 아닌 값을 반환 하 고 그렇지 않으면 0 ()을 반환 `FALSE` 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 Null 참조는 빈 개체 또는에 할당 되지 않은 개체를 의미 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e4b6e5f2d28d27deb5e4e1ff8278a071ff9110fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726521"
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

## <a name="see-also"></a>추가 정보
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

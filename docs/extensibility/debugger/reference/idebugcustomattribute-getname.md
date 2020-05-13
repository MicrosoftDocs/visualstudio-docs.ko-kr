---
title: IDebug사용자 속성::GetName | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 15d435d043d0e3863358628fa12016431a417918
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732765"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
사용자 지정 특성의 이름을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetName( 
   BSTR* bstrName
);
```

```csharp
int GetName(
   out string bstrName
);
```

## <a name="parameters"></a>매개 변수
`bstrName`\
【아웃】 사용자 지정 특성의 이름을 포함하는 문자열을 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드에서 반환 된 명명 된 특성을 선언 하는 데 사용 하는 클래스의 이름에 해당 합니다. C#을 사용하면 선언에 사용될 때 사용자 지정 특성 이름에서 "특성" 접미사를 삭제할 수 있으므로 사용자 지정 특성 클래스 자체의 이름과 정확히 일치하지 않을 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)

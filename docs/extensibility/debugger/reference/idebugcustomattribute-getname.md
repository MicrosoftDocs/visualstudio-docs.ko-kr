---
title: 'IDebugCustomAttribute:: GetName | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
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
제한이 사용자 지정 특성의 이름을 포함 하는 문자열을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드에서 반환 되는 이름은 특성을 선언 하는 데 사용 되는 클래스의 이름에 해당 합니다. 이는 선언에 사용 될 때 사용자 지정 특성 이름에서 "특성" 접미사를 삭제할 수 있으므로 사용자 지정 특성 클래스 자체의 이름과 정확 하 게 일치 하지 않을 수 있습니다.

## <a name="see-also"></a>추가 정보
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)

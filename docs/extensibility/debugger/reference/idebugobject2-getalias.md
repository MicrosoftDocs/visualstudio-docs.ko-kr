---
title: 'IDebugObject2:: GetAlias | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 53c72182b497e2b24d41a784c405d169c3db195f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726280"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
이 개체와 연결 된 별칭을 가져옵니다 (있는 경우).

## <a name="syntax"></a>구문

```cpp
HRESULT GetAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int GetAlias(
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>매개 변수
`ppAlias`\
제한이 이 개체의 별칭을 나타내는 [Idebugalias](../../../extensibility/debugger/reference/idebugalias.md) 개체를 반환 합니다. 그렇지 않으면 null 값을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 [Createalias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) 메서드를 호출 하 여 개체에 대 한 별칭을 만듭니다.

## <a name="see-also"></a>추가 정보
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)

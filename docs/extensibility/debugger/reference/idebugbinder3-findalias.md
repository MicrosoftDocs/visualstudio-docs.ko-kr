---
title: 이데버그바인더3::파인알리아스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0a697e39d21b1c25a98c09ad6cc4837cca7a293
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735870"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
이 메서드는 이름에 따라 별칭을 찾습니다. 그러면 프로그램의 모든 별칭이 검색됩니다.

## <a name="syntax"></a>구문

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>매개 변수
`pcstrName`\
【인】 찾을 별칭의 이름입니다.

`ppAlias`\
【아웃】 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) 인터페이스로 표시되는 별칭(있는 경우)을 찾습니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 `S_FALSE` (별칭을 찾을 수 없는 경우) 또는 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드는 호출 하기 전에 null대상 오브젝트를 초기화 합니다. 그런 다음 나중에 null 값을 테스트하여 별칭이 발견되었는지 여부를 확인합니다.

## <a name="see-also"></a>참조
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)

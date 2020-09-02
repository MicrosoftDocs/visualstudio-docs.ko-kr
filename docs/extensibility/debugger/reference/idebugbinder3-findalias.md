---
title: 'IDebugBinder3:: FindAlias | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735870"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
이 메서드는 이름이 지정 된 별칭을 찾습니다. 프로그램의 모든 별칭을 검색 합니다.

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
진행 찾을 별칭의 이름입니다.

`ppAlias`\
제한이 [Idebugalias](../../../extensibility/debugger/reference/idebugalias.md) 인터페이스로 표시 된 별칭이 있습니다 (있는 경우).

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 `S_FALSE` (별칭을 찾을 수 없는 경우) 또는 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는를 호출 하기 전에 대상 개체를 null로 초기화 합니다. 그런 다음 나중에 null 값을 테스트 하 여 별칭을 찾을 수 있는지 여부를 확인 합니다.

## <a name="see-also"></a>추가 정보
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)

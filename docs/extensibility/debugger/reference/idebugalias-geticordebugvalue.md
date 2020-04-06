---
title: 이데버그알리아스::겟디코르데버그 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd01785fee7ce65296bac940fb19819415139d53
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736484"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
이 별칭과 연결된 값을 나타내는 관리되는 코드 인터페이스를 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>매개 변수
`ppUnk`\
【아웃】 `IUnknown` 이 별칭과 연관된 값을 나타내는 인터페이스입니다. 이 인터페이스는 인터페이스에 `ICorDebugValue` 대해 쿼리할 수 있습니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 `ICorDebugValue` 메서드는 관리되는 값에만 적용됩니다(.NET Framework에서 사용할 수 있는 인터페이스이며 cordebug.idl 파일의 .NET Framework SDK에 정의되어 있음).

## <a name="see-also"></a>참조
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)

---
description: 이 별칭과 연결 된 값을 나타내는 관리 되는 코드 인터페이스를 검색 합니다.
title: 'IDebugAlias:: GetICorDebugValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad6cd04d077245d3e893099aab8820ddc8ccf559
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095916"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
이 별칭과 연결 된 값을 나타내는 관리 되는 코드 인터페이스를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>매개 변수
`ppUnk`\
[out] `IUnknown` 이 별칭과 연결 된 값을 나타내는 인터페이스입니다. 인터페이스에 대해이 인터페이스를 쿼리할 수 있습니다 `ICorDebugValue` .

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드는 관리 되는 값에만 적용 됩니다 `ICorDebugValue` .는 .NET Framework에서 사용할 수 있는 인터페이스 이며 cordebug .idl 파일의 .NET FRAMEWORK SDK에 정의 되어 있습니다.

## <a name="see-also"></a>참조
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)

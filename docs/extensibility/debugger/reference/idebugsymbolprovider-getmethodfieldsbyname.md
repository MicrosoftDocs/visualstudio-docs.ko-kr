---
description: 이 메서드는 정규화 된 메서드 이름을 나타내는 필드를 가져옵니다.
title: 'Idebug Provider:: GetMethodFieldsByName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetMethodFieldsByName
helpviewer_keywords:
- IDebugSymbolProvider::GetMethodFieldsByName method
ms.assetid: 1f781320-81ef-4037-b068-f1864b271258
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 54962d87bcb3de471c9799f4c6be9f969b8eed17
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087004"
---
# <a name="idebugsymbolprovidergetmethodfieldsbyname"></a>IDebugSymbolProvider::GetMethodFieldsByName
이 메서드는 정규화 된 메서드 이름을 나타내는 필드를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetMethodFieldsByName( 
   LPCOLESTR          pszFullName,
   NAME_MATCH         nameMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int GetMethodFieldsByName(
   string               pszFullName,
   NAME_MATCH           nameMatch,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>매개 변수
`pszFullName`\
진행 메서드 이름입니다.

`nameMatch`\
진행 일치 유형 (예: 대/소문자 구분)을 선택 합니다.

`ppEnum`\
제한이 이 메서드와 연결 된 필드에 대 한 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 열거자를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 예를 들어 오버 로드 된 경우 여러 필드에 메서드를 연결할 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)

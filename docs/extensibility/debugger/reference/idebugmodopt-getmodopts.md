---
description: 선택적 한정자 목록을 검색 합니다.
title: 'IDebugModOpt:: GetModOpts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 614ecb456b6f644dfd389020bbffb23691cfbf43
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081908"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
선택적 한정자 목록을 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetModOpts(
   ULONG  celt,
   BSTR*  rgelt,
   ULONG* pceltFetched
);
```

```csharp
int GetModOpts(
   uint         celt,
   out string[] rgelt,
   ref uint     pceltFetched
);
```

## <a name="parameters"></a>매개 변수
`celt`\
진행 반환 되는 요소 수입니다.

`rgelt`\
제한이 옵션이 포함 된 배열을 반환 합니다.

`pceltFetched`\
[in, out] 배열에서 반환 된 요소의 수 `rgelt` 입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참조
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)

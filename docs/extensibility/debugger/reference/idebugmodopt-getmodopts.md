---
description: 선택적 한정자 목록을 검색 합니다.
title: 'IDebugModOpt:: GetModOpts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 971d04662042afed1afe8e1861d0080b513ca74d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149940"
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

## <a name="see-also"></a>참고 항목
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)

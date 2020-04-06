---
title: 이데버그모드옵트::겟모드옵스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ab870db3ae3517b60bebd4815e4530f6035b327
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727055"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
선택적 수정자 목록을 검색합니다.

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
【인】 반환할 요소 수입니다.

`rgelt`\
【아웃】 옵션이 포함된 배열을 반환합니다.

`pceltFetched`\
【인, 아웃】 배열에서 반환되는 `rgelt` 요소 수입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)

---
title: IEnumDebugCodeContexts2::건너뛰기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2::Skip
helpviewer_keywords:
- IEnumDebugCodeContexts2::Skip
ms.assetid: 3451a3eb-bf5b-4ec5-acc9-aa5a24363801
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6a1f63f5e3a6a84d6752707de5c81b4549085662
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717318"
---
# <a name="ienumdebugcodecontexts2skip"></a>IEnumDebugCodeContexts2::Skip
지정된 수의 요소를 건너뜁니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Skip(
   ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

## <a name="parameters"></a>매개 변수
`celt`\
【인】 건너뛸 요소 수입니다.

## <a name="return-value"></a>Return Value
 성공하면 `S_OK`를 반환합니다. 나머지 `S_FALSE` `celt` 요소 의 수보다 큰 경우 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 나머지 `celt` 요소 수보다 큰 값을 지정하면 열거형이 끝으로 설정되고 `S_FALSE` 반환됩니다.

## <a name="see-also"></a>참조
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)

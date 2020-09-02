---
title: 'IEnumDebugObjects:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Skip
helpviewer_keywords:
- IEnumDebugObjects::Skip method
ms.assetid: 957cead8-0a9c-4403-b190-b9fbadc49d42
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 80d2ae53ea7732a2120cf0431f33f929a0a6bc05
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80716277"
---
# <a name="ienumdebugobjectsskip"></a>IEnumDebugObjects::Skip
이 메서드는 지정 된 수의 요소를 건너뜁니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Skip(
   [in] ULONG celt
);
```

```csharp
int Skip(
   [In] uint celt
);
```

## <a name="parameters"></a>매개 변수
`celt`\
진행 건너뛸 요소 수입니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. `S_FALSE` `celt` 가 나머지 요소 수보다 크면를 반환 하 고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 가 `celt` 나머지 요소 수보다 큰 값을 지정 하는 경우 열거형은 end로 설정 되 고 `S_FALSE` 이 반환 됩니다.

## <a name="see-also"></a>추가 정보
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)

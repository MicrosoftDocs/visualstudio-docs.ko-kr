---
title: 'IEnumDebugCustomAttributes:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Next
helpviewer_keywords:
- IEnumDebugCustomAttributes::Next
ms.assetid: e36f856b-2619-42d1-b73e-4f2390fc22bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08228fe4a630eac37c38f4eb247dc91678d8e2e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80717240"
---
# <a name="ienumdebugcustomattributesnext"></a>IEnumDebugCustomAttributes::Next
열거형 시퀀스에서 지정 된 수의 사용자 지정 특성을 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Next ( 
   ULONG      celt,
   CODE_PATH* rgelt,
   ULONG*     pceltFetched
);
```

```csharp
int Next(
   uint                        celt,
   out IDebugCustomAttribute[] rgelt,
   ref uint                    pceltFetched
);
```

## <a name="parameters"></a>매개 변수
`celt`\
진행 검색할 요소의 수입니다. 또한 배열의 최대 크기를 지정 합니다 `rgelt` .

`rgelt`\
제한이 채워질 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) 개체의 배열입니다.

`pceltFetched`\
제한이 에서 실제로 반환 된 요소의 수를 반환 합니다 `rgelt` .

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. `S_FALSE`요청 된 수의 요소를 반환할 수 있으면를 반환 하 고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>추가 정보
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)

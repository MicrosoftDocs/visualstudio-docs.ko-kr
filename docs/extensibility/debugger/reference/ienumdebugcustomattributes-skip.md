---
description: 열거형 시퀀스에서 지정 된 수의 사용자 지정 특성을 건너뜁니다.
title: 'IEnumDebugCustomAttributes:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Skip
helpviewer_keywords:
- IEnumDebugCustomAttributes::Skip
ms.assetid: 54c72e23-cd4c-4746-935c-abea8057dd1b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 07a252203e2c3cfa2194a14cea8ea576bb2683fb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091723"
---
# <a name="ienumdebugcustomattributesskip"></a>IEnumDebugCustomAttributes::Skip
열거형 시퀀스에서 지정 된 수의 사용자 지정 특성을 건너뜁니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Skip ( 
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
진행 건너뛸 요소 수입니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. `S_FALSE` `celt` 가 나머지 요소 수보다 크면를 반환 하 고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 가 `celt` 나머지 요소 수보다 큰 값을 지정 하는 경우 열거형은 end로 설정 되 고 `S_FALSE` 이 반환 됩니다.

## <a name="see-also"></a>참조
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)

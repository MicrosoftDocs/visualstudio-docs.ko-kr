---
description: 현재 DEBUG_PROPERTY_INFO 열거형의 복사본을 별도의 개체로 반환 합니다.
title: 'IEnumDebugPropertyInfo2:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2::Clone
helpviewer_keywords:
- IEnumDebugPropertyInfo2::Clone
ms.assetid: 0ede1667-1071-4aa4-b887-260ea103d724
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79f5ffd45799b8c2c2ed1642004c26889b26c172
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082922"
---
# <a name="ienumdebugpropertyinfo2clone"></a>IEnumDebugPropertyInfo2::Clone
현재 열거형의 복사본을 별도의 개체로 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Clone(
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>매개 변수
`ppEnum`\
제한이 이 열거형의 복사본을 별도의 개체로 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 열거형의 복사본은이 메서드가 호출 될 때의 원래 상태와 동일 합니다. 그러나 복사본과 원래 상태는 별개 이며 개별적으로 변경할 수 있습니다.

## <a name="see-also"></a>참조
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)

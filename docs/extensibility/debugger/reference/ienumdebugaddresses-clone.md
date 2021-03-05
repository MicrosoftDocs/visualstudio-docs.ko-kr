---
description: 이 메서드는 현재 주소 열거의 복사본을 별도의 개체로 반환 합니다.
title: 'IEnumDebugAddresses:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Clone
helpviewer_keywords:
- IEnumDebugAddresses::Clone method
ms.assetid: 71189a00-34eb-4c71-b96e-8bd6e70c6966
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bf78bc1964c3498b845a2e1f89235d7c572b1916
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225138"
---
# <a name="ienumdebugaddressesclone"></a>IEnumDebugAddresses::Clone
이 메서드는 현재 열거형의 복사본을 별도의 개체로 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Clone(
   IEnumDebugAddresses** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugAddresses ppEnum
);
```

## <a name="parameters"></a>매개 변수
`ppEnum`\
제한이 이 열거형의 복사본을 별도의 개체로 반환 합니다.

## <a name="property-valuereturn-value"></a>속성 값/반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 열거형의 복사본은이 메서드가 호출 될 때의 원래 상태와 동일 합니다. 그러나 복사본과 원래 상태는 별개 이며 개별적으로 변경할 수 있습니다.

## <a name="see-also"></a>참고 항목
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)

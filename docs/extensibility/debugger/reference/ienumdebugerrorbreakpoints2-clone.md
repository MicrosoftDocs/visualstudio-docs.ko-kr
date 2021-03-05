---
description: 현재 오류 중단점 열거형의 복사본을 별도의 개체로 반환 합니다.
title: 'IEnumDebugErrorBreakpoints2:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2::Clone
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2::Clone
ms.assetid: f6fb4985-8dd6-4a9b-98e0-15dbc64cc9ec
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f0f42ff6c6faef0ebe05f5f98445b6c51aa5152
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226815"
---
# <a name="ienumdebugerrorbreakpoints2clone"></a>IEnumDebugErrorBreakpoints2::Clone
현재 열거형의 복사본을 별도의 개체로 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Clone(
   IEnumDebugErrorBreakpoints2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugErrorBreakpoints2 ppEnum
);
```

## <a name="parameters"></a>매개 변수
`ppEnum`\
제한이 이 열거형의 복사본을 별도의 개체로 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 열거형의 복사본은이 메서드가 호출 될 때의 원래 상태와 동일 합니다. 그러나 복사본과 원래 상태는 별개 이며 개별적으로 변경할 수 있습니다.

## <a name="see-also"></a>참고 항목
- [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)

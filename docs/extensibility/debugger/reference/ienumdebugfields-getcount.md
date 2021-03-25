---
description: 이 메서드는 필드 열거의 요소 수를 반환 합니다.
title: 'IEnumDebugFields:: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::GetCount
helpviewer_keywords:
- IEnumDebugFields::GetCount method
ms.assetid: 3f471b40-4db3-49f7-b504-58b2476eef74
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a3b2512364ffb8642cb4ebc763d690514ff5fc11
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105052933"
---
# <a name="ienumdebugfieldsgetcount"></a>IEnumDebugFields::GetCount
이 메서드는 열거형의 요소 수를 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetCount(
   [out] ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>매개 변수
`pcelt`\
제한이 열거형의 요소 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 다음, 복제, 건너뛰기 및 다시 설정을 구현 해야 하도록 지정 하는 일반적인 COM 열거 인터페이스의 일부가 아닙니다.

## <a name="see-also"></a>참조
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)

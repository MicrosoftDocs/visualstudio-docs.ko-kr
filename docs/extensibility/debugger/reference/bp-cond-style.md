---
description: 보류 중인 중단점과 바인딩된 중단점의 중단점 조건 스타일을 지정 합니다.
title: BP_COND_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 611df036ff876e10096013070cac097bc51a8986
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085418"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
보류 중인 중단점과 바인딩된 중단점의 중단점 조건 스타일을 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
typedef DWORD BP_COND_STYLE;
```

```csharp
public enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
```

## <a name="fields"></a>필드
`BP_COND_NONE`\
중단점의 위치에 도달 하면 중단점을 발생 시킵니다. 중단점 조건이 지정 되지 않았습니다.

`BP_COND_WHEN_TRUE`\
중단점과 연결 된 조건식이로 평가 되는 경우에만 중단점을 발생 시킵니다 `true` .

`BP_COND_WHEN_CHANGED`\
중단점과 연결 된 조건부 식의 값이 이전 계산에서 변경 된 경우에만 중단점을 발생 시킵니다.

## <a name="remarks"></a>설명
`styleCondition` [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) 구조체의 멤버에 사용 됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)

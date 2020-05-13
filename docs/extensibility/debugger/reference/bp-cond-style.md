---
title: BP_COND_STYLE | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca704ca186308ea9e44c4fa7edc6617cbac806eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738119"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
보류 중인 중단점 및 바인딩된 중단점에 대한 중단점 조건 스타일을 지정합니다.

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
중단점의 위치에 도달하면 중단점을 발생시면 중단점을 발생시면 중단점 조건을 지정하지 않았습니다.

`BP_COND_WHEN_TRUE`\
중단점과 연결된 조건식이 로 평가될 `true`때만 중단점을 발생시면 중단점이 발생합니다.

`BP_COND_WHEN_CHANGED`\
중단점과 연결된 조건부 식값이 이전 평가에서 변경된 경우에만 중단점을 발생시면 중단점을 발생시면 됩니다.

## <a name="remarks"></a>설명
`styleCondition` [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) 구조의 부재에 사용됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)

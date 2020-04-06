---
title: BP_PASSCOUNT_STYLE | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1633c5e9aa6ff251fedce83a0243664cd9e0e0a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737920"
---
# <a name="bp_passcount_style"></a>BP_PASSCOUNT_STYLE
중단점이 발생한 중단점 통과 수와 연관된 조건을 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
typedef DWORD BP_PASSCOUNT_STYLE;
```

```csharp
public enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
```

## <a name="fields"></a>필드
`BP_PASSCOUNT_NONE`\
중단점 통과 카운트 스타일을 지정하지 않습니다.

`BP_PASSCOUNT_EQUAL`\
중단점 통과 개수 스타일을 같게 설정합니다. 중단점이 적중된 횟수가 패스 수와 같을 때 중단점이 발생합니다.

`BP_PASSCOUNT_EQUAL_OR_GREATER`\
중단점 통과 개수 스타일을 같거나 더 큰 것으로 설정합니다. 중단점이 적중된 횟수가 합격수와 같거나 클 때 중단점이 발생합니다.

`BP_PASSCOUNT_MOD`\
조절 패스 수를 지정합니다. 예를 들어 패스 수가 형식이고 `BP_PASSCOUNT_MOD` 패스 카운트 값이 4인 경우 적중 수가 4의 배수일 때마다 중단점이 발생합니다.

## <a name="remarks"></a>설명
BP_PASSCOUNT [구조의](../../../extensibility/debugger/reference/bp-passcount.md) `stylePassCount` 부재에 사용되며, 이는 차례로 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) [및 BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 구조의 부재이다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)

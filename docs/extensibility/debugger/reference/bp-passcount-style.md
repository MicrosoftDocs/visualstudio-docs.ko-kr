---
title: BP_PASSCOUNT_STYLE | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737920"
---
# <a name="bp_passcount_style"></a>BP_PASSCOUNT_STYLE
중단점이 실행 되도록 하는 중단점 패스 개수와 연결 된 조건을 지정 합니다.

## <a name="syntax"></a>Syntax

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
중단점 패스 개수 스타일을 지정 하지 않습니다.

`BP_PASSCOUNT_EQUAL`\
중단점 패스 개수 스타일을 같게 설정 합니다. 중단점은 중단점이 적중 된 횟수와 패스 개수가 일치 하는 경우에 발생 합니다.

`BP_PASSCOUNT_EQUAL_OR_GREATER`\
중단점 패스 개수 스타일을 같거나 더 큼으로 설정 합니다. 중단점은 중단점이 적중 된 횟수가 패스 개수 보다 크거나 같은 경우에 발생 합니다.

`BP_PASSCOUNT_MOD`\
모듈로 패스 수를 지정 합니다. 예를 들어, 패스 수가 형식이 `BP_PASSCOUNT_MOD` 고 pass count 값이 4 인 경우 적중 횟수가 4의 배수가 될 때마다 중단점이 발생 합니다.

## <a name="remarks"></a>설명
`stylePassCount` [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 및 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 구조체의 멤버를 사용 하는 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) 구조체의 멤버에 사용 됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)

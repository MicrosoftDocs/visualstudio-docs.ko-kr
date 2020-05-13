---
title: DOCCONTEXT_COMPARE | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75e4453cae63f484961cb2d0f3385a703709f83b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737235"
---
# <a name="doccontext_compare"></a>DOCCONTEXT_COMPARE
두 문서 컨텍스트 비교 기준을 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
typedef DWORD DOCCONTEXT_COMPARE;
```

```csharp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
```

## <a name="fields"></a>필드
`DOCCONTEXT_EQUAL`\
대상 문서 컨텍스트와 동일한 목록에서 첫 번째 문서 컨텍스트를 찾습니다.

`DOCCONTEXT_LESS_THAN`\
대상 문서 컨텍스트보다 적은 목록에서 첫 번째 문서 컨텍스트를 찾습니다.

`DOCCONTEXT_GREATER_THAN`\
대상 문서 컨텍스트보다 큰 목록에서 첫 번째 문서 컨텍스트를 찾습니다.

`DOCCONTEXT_SAME_DOCUMENT`\
대상 문서 컨텍스트와 동일한 문서에 있는 목록에서 첫 번째 문서 컨텍스트를 찾습니다.

## <a name="remarks"></a>설명
[비교](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) 메서드에 인수로 전달되었습니다.

이러한 값은 목록에서 첫 번째 문서 컨텍스트를 찾기 위한 비교 기준을 지정하는 데 사용됩니다. 문서 컨텍스트에는 `IDebugDocumentContext2::Compare` 메서드를 통해 자신을 비교하는 문서 컨텍스트 목록이 제공됩니다. 그런 다음 비교 연산자가 있는 목록의 첫 번째 문서 컨텍스트가 반환됩니다. `true`

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [비교](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)

---
title: DOCCONTEXT_COMPARE | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737235"
---
# <a name="doccontext_compare"></a>DOCCONTEXT_COMPARE
두 문서 컨텍스트를 비교 하는 조건을 지정 합니다.

## <a name="syntax"></a>Syntax

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
목록에서 대상 문서 컨텍스트와 동일한 첫 번째 문서 컨텍스트를 찾습니다.

`DOCCONTEXT_LESS_THAN`\
목록에서 대상 문서 컨텍스트 보다 작은 첫 번째 문서 컨텍스트를 찾습니다.

`DOCCONTEXT_GREATER_THAN`\
목록에서 대상 문서 컨텍스트 보다 큰 첫 번째 문서 컨텍스트를 찾습니다.

`DOCCONTEXT_SAME_DOCUMENT`\
목록에서 대상 문서 컨텍스트와 동일한 문서에 있는 첫 번째 문서 컨텍스트를 찾습니다.

## <a name="remarks"></a>설명
[Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) 메서드에 인수로 전달 됩니다.

이러한 값은 목록에서 첫 번째 문서 컨텍스트를 찾기 위한 비교 조건을 지정 하는 데 사용 됩니다. 문서 컨텍스트에는 메서드를 통해 자신을 비교 하는 문서 컨텍스트 목록이 제공 됩니다 `IDebugDocumentContext2::Compare` . 비교 연산자가 반환 되는 목록에서 첫 번째 문서 컨텍스트입니다 `true` .

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [비교](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)

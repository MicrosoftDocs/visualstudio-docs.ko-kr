---
title: PARSEFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78890f088646842435198fa839c0f88cba5483b9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880192"
---
# <a name="parseflags"></a>PARSEFLAGS
식을 구문 분석 하는 방법을 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
typedef DWORD PARSEFLAGS;
```

```csharp
public enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
```

## <a name="fields"></a>필드
 `PARSE_EXPRESSION`\
 식이 문이 아님을 나타냅니다.

 `PARSE_FUNCTION_AS_ADDRESS`\
 식을 주소로 구문 분석 하 고 나중에 계산 하도록 지정 합니다.

 `PARSE_DESIGN_TIME_EXPR_EVAL`\
 디자인 타임 중에 식이 구문 분석 되 고 있음을 나타냅니다 (즉, 디자이너가 열려 있는 경우).

## <a name="remarks"></a>설명
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 및 [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 메서드에 매개 변수로 전달 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)

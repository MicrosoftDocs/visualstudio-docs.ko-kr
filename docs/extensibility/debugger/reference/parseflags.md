---
title: 파르세 플래그 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0cc70fdd9fe1279e4d419a422b970eb3d3b07c65
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714113"
---
# <a name="parseflags"></a>PARSEFLAGS
식을 구문 분석하는 방법을 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
typedef DWORD PARSEFLAGS;
```

```csharp
public enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
```

## <a name="fields"></a>필드
 `PARSE_EXPRESSION`\
 식이 문이 아님을 나타냅니다.

 `PARSE_FUNCTION_AS_ADDRESS`\
 식을 구문 분석(나중에 평가)할 수 있음을 나타냅니다.

 `PARSE_DESIGN_TIME_EXPR_EVAL`\
 표현식이 디자인 시간(즉, 디자이너가 열려 있는 경우)에 구문 분석중임을 나타냅니다.

## <a name="remarks"></a>설명
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 및 [구문 분석](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 메서드에 매개 변수로 전달되었습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [구문 분석](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)

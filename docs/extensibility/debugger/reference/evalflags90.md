---
title: 에발플래그90 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01951885541ba4acce33f3e4f06f7106116ccc62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737095"
---
# <a name="evalflags90"></a>EVALFLAGS90
식 평가를 제어하는 플래그에 대한 유효한 값을 개수합니다. 이 열거형은 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 열거를 확장합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
typedef DWORD EVALFLAGS90;
```

```csharp
public enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
```

## <a name="fields"></a>필드
`EVAL90_RETURNVALUE`\
반환 값(있는 경우)을 평가할 수 있도록 지정합니다.

`EVAL90_NOSIDEEFFECTS`\
부작용이 허용되지 않도록 지정합니다.

`EVAL90_ALLOWBPS`\
중단점에 중지를 지정합니다.

`EVAL90_ALLOWERRORREPORT`\
호스트에 대한 오류 보고가 허용되도록 지정합니다. 주로 Internet Explorer의 스크립트에서 식 평가에 사용됩니다.

`EVAL90_FUNCTION_AS_ADDRESS`\
함수를 호출하는 대신 주소로 평가할 강제로 함수를 강제합니다.

`EVAL90_NOFUNCEVAL`\
함수가 평가되는 것을 방지합니다. 예를 들어 식의 `int` 토큰을 `myExpression(int) + 10`고려합니다. 이 함수는 주소로 올바르게 평가할 수 있지만 값으로 는 평가할 수 없습니다.

`EVAL90_NOEVENTS`\
표현식 평가 중에 발생하는 이벤트가 세션 디버그 관리자(SDM) 또는 IDE로 전송되어서는 안 된다는 것을 나타냅니다.

`EVAL90_DESIGN_TIME_EXPR_EVAL`\
디자인-시간 식 평가를 활성화합니다.

`EVAL90_ALLOW_IMPLICIT_VARS`\
암시적 변수 생성을 허용합니다.

`EVAL90_FORCE_EVALUATION_NOW`\
즉시 평가가 수행되도록 강제합니다. 이 기능은 사용자 요청과 같은 요청을 서비스할 때 유용합니다.

## <a name="requirements"></a>요구 사항
헤더: Msdbg90.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

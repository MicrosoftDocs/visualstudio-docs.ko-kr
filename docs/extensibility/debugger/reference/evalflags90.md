---
title: EVALFLAGS90 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737095"
---
# <a name="evalflags90"></a>EVALFLAGS90
식 계산을 제어 하는 플래그에 대 한 유효한 값을 열거 합니다. 이 열거형은 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 열거형을 확장 합니다.

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
반환 값 (있는 경우)을 계산 하도록 지정 합니다.

`EVAL90_NOSIDEEFFECTS`\
의도 하지 않은 결과를 허용 하지 않도록 지정 합니다.

`EVAL90_ALLOWBPS`\
중단점에 대 한 중지를 지정 합니다.

`EVAL90_ALLOWERRORREPORT`\
호스트에 대 한 오류 보고를 허용 하도록 지정 합니다. 주로 Internet Explorer의 스크립트에서 식 계산에 사용 됩니다.

`EVAL90_FUNCTION_AS_ADDRESS`\
함수를 호출 하는 대신 함수를 주소로 계산 합니다.

`EVAL90_NOFUNCEVAL`\
함수가 계산 되지 않도록 합니다. 예를 들어 `int` 식의 토큰을 고려 `myExpression(int) + 10` 합니다. 이 함수는 값이 아니라 주소로 올바르게 계산 될 수 있습니다.

`EVAL90_NOEVENTS`\
식 평가 중에 발생 하는 이벤트를 세션 디버그 관리자 (SDM) 또는 IDE로 보내지 않아야 함을 나타내는 플래그입니다.

`EVAL90_DESIGN_TIME_EXPR_EVAL`\
디자인 타임 식 계산을 사용 합니다.

`EVAL90_ALLOW_IMPLICIT_VARS`\
암시적 변수 생성을 허용 합니다.

`EVAL90_FORCE_EVALUATION_NOW`\
계산이 즉시 수행 되도록 합니다. 사용자 요청과 같은 요청을 서비스 하는 경우에 유용 합니다.

## <a name="requirements"></a>요구 사항
헤더: Msdbg90

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

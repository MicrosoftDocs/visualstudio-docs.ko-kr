---
title: CANSTOP_REASON | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d7be361d4468584c109db52f487b3de3c1fdff0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737685"
---
# <a name="canstop_reason"></a>CANSTOP_REASON
프로그램이 실행의 특정 지점에 도달한 후 실행을 중지할 수 있는지 확인하는 데 사용됩니다.

## <a name="syntax"></a>구문

```cpp
enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
typedef DWORD CANSTOP_REASON;
```

```csharp
public enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
```

## <a name="fields"></a>필드
`CANSTOP_ENTRYPOINT`\
지정된 프로그램의 진입점을 지정합니다.

`CANSTOP_STEPIN`\
함수에 스테핑을 지정합니다.

## <a name="remarks"></a>설명
프로그램의 진입점에 도달한 후 또는 함수 또는 메서드에 들어간 후 중지해도 되는 경우 세션 디버그 관리자(SDM)를 확인하려면 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) 메서드에 인수로 전달됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)

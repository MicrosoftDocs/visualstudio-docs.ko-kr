---
title: EXCEPTION_STATE | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cd2e280cd03ae413e0853950d13fbfefb69bc15f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736963"
---
# <a name="exception_state"></a>EXCEPTION_STATE
예외 상태를 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
typedef DWORD EXCEPTION_STATE;
```

```csharp
public enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
```

## <a name="fields"></a>필드
`EXCEPTION_NONE`\
예외에서 멈추지 마십시오.

`EXCEPTION_STOP_FIRST_CHANCE`\
예외의 첫 번째 발사에서 중지합니다. 예외 이벤트를 설명할 때 이 플래그는 예외 이벤트가 첫 번째 예외 이벤트임을 나타냅니다.

`EXCEPTION_STOP_SECOND_CHANCE`\
예외의 두 번째 발사에서 중지합니다. 예외 이벤트를 설명할 때 예외 이벤트가 두 번째 예외 이벤트임을 나타냅니다.

`EXCEPTION_STOP_USER_FIRST_CHANCE`\
사용자 모드 예외의 첫 번째 실행에서 중지합니다. 예외 이벤트를 설명할 때 예외 이벤트가 첫 번째 사용자 예외 이벤트임을 나타냅니다.

`EXCEPTION_STOP_USER_UNCAUGHT`\
사용자 모드 예외가 catch되지 않은 경우 중지합니다. 예외 이벤트를 설명할 때 예외 이벤트가 catch되지 않은 사용자 모드 예외 이벤트임을 나타냅니다.

`EXCEPTION_STOP_ALL`\
예외를 중지합니다. 예외 이벤트를 설명할 때는 사용되지 않습니다.

`EXCEPTION_CANNOT_BE_CONTINUED`\
예외 이벤트를 설명할 때 예외를 계속 실행할 수 없음을 나타냅니다.

`EXCEPTION_CODE_SUPPORTED`\
예외에 이를 지원하는 코드가 있음을 나타냅니다. 예외 표시에 사용

`EXCEPTION_CODE_DISPLAY_IN_HEX`\
예외 코드가 육각형에 표시되어야 음을 나타냅니다. 예외를 표시하는 데 사용됩니다.

`EXCEPTION_JUST_MY_CODE_SUPPORTED`\
예외 코드가 JustMyCode를 지원한다는 것을 나타냅니다. 예외를 표시하는 데 사용됩니다.

`EXCEPTION_MANAGED_DEBUG_ASSISTANT`\
관리 되는 코드 디버거 예외를 처리 해야 합니다 나타냅니다. 설정하지 않으면 기본 디버거가 예외를 처리합니다. 이는 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) 메서드에 전달되며 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) 구조에서는 사용되지 않습니다.

`EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT`\
더 이상 사용되지 마십시오.

`EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT`\
더 이상 사용되지 마십시오.

`EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT`\
더 이상 사용되지 마십시오.

`EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT`\
더 이상 사용되지 마십시오.

## <a name="remarks"></a>설명
`dwState` [예외의](../../../extensibility/debugger/reference/exception-info.md) 상태와 EXCEPTION_INFO 구성에 대해 수행할 수 있는 작업을 나타내는 EXCEPTION_INFO 구조의 멤버로 사용됩니다.

이러한 값은 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) 메서드에 전달되어 모든 예외의 상태를 설정합니다.

이러한 플래그는 비트 OR와 결합될 수 있습니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)

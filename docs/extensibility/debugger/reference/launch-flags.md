---
description: 디버그 시작 플래그를 지정 합니다.
title: LAUNCH_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- LAUNCH_FLAGS
helpviewer_keywords:
- LAUNCH_FLAGS enumeration
ms.assetid: f51aab02-d257-4302-bb79-b7d8ba9ac4e5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e12dc587a77e428d3d4c4740043ab5651b7897a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058003"
---
# <a name="launch_flags"></a>LAUNCH_FLAGS
디버그 시작 플래그를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_LAUNCH_FLAGS {
    LAUNCH_DEBUG      = 0x0000,
    LAUNCH_NODEBUG    = 0x0001,
    LAUNCH_ENABLE_ENC = 0x0002,
    LAUNCH_MERGE_ENV  = 0x0004
};
typedef DWORD LAUNCH_FLAGS;
```

```csharp
public enum enum_LAUNCH_FLAGS {
    LAUNCH_DEBUG      = 0x0000,
    LAUNCH_NODEBUG    = 0x0001,
    LAUNCH_ENABLE_ENC = 0x0002,
    LAUNCH_MERGE_ENV  = 0x0004
};
```

## <a name="fields"></a>필드
`LAUNCH_DEBUG`\
디버깅 프로세스를 시작 합니다.

`LAUNCH_NODEBUG`\
디버깅 하지 않고 프로세스를 시작 합니다.

`LAUNCH_ENABLE_ENC`\
사용 되지 않습니다 .를 사용 하지 마십시오.

`LAUNCH_MERGE_ENV`\
프로세스를 시작 하 고 환경을 시작 호스트와 병합 합니다.

## <a name="remarks"></a>설명
이러한 값은 [Launchsuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) 메서드에 인수로 전달 됩니다.

이러한 플래그는 비트와 함께 사용할 수 있습니다 `OR` .

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)

---
title: 스레드 상태 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1b291cc1668b2b867729da11d4c561f74567f257
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713333"
---
# <a name="threadstate"></a>THREADSTATE
스레드의 상태를 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
typedef DWORD THREADSTATE;
```

```csharp
public enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
```

## <a name="fields"></a>필드
 `THREADSTATE_RUNNING`\
 스레드가 실행 중임을 나타냅니다.

 `THREADSTATE_STOPPED`\
 중단점으로 인해 스레드가 중지됨을 나타냅니다.

 `THREADSTATE_FRESH`\
 스레드가 만들어졌지만 아직 코드를 실행하지 않음을 나타냅니다.

 `THREADSTATE_DEAD`\
 스레드가 죽었음을 나타냅니다.

 `THREADSTATE_FROZEN`\
 스레드가 고정됨을 나타냅니다(실행을 수행할 수 없음).

## <a name="remarks"></a>설명
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) `dwThreadState` 구조의 필드에 사용됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)

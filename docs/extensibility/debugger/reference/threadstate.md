---
description: 스레드의 상태를 지정 합니다.
title: THREADSTATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 513e90e649d71a4fb7d5bc220eb9752925151d9f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070819"
---
# <a name="threadstate"></a>THREADSTATE
스레드의 상태를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
typedef DWORD THREADSTATE;
```

```csharp
public enum enum_THREADSTATE { 
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
 중단점 때문에 스레드가 중지 되었음을 나타냅니다.

 `THREADSTATE_FRESH`\
 스레드가 만들어졌지만 아직 코드를 실행 하 고 있지 않음을 나타냅니다.

 `THREADSTATE_DEAD`\
 스레드가 비활성 상태임을 나타냅니다.

 `THREADSTATE_FROZEN`\
 스레드가 고정 됨을 나타냅니다 (실행을 수행할 수 없음).

## <a name="remarks"></a>설명
 `dwThreadState` [Threadproperties](../../../extensibility/debugger/reference/threadproperties.md) 구조의 필드에 사용 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)

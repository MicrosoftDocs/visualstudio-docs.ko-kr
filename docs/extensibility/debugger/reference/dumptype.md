---
title: 덤프타입 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0d4d42709efdefe097b4c8a78a0b00f45f2e1a2b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737208"
---
# <a name="dumptype"></a>DUMPTYPE
덤프할 프로그램의 상태(예: 실행 중인 스레드, 스택 프레임 및 현재 명령 어누)를 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_DUMPTYPE {
    DUMP_MINIDUMP = 0,
    DUMP_FULLDUMP = 1
};
typedef DWORD DUMPTYPE;
```

```csharp
public enum enum_DUMPTYPE {
    DUMP_MINIDUMP = 0,
    DUMP_FULLDUMP = 1
};
```

## <a name="fields"></a>필드
`DUMP_MINIDUMP`\
작고 컴팩트한 덤프를 지정합니다.

`DUMP_FULLDUMP`\
크고 완전한 덤프를 지정합니다.

## <a name="remarks"></a>설명
[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) 메서드에 인수로 전달 되었습니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)

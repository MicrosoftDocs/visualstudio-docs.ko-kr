---
title: 문자 형식 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 99e7e5a9e092118eb40501e6f2ba3cc580cf7cc7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953736"
---
# <a name="dumptype"></a>DUMPTYPE
덤프 하는 프로그램의 상태 (예: 실행 중인 스레드, 스택 프레임 및 현재 명령 주소)의 양을 지정 합니다.

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
작은 압축 덤프를 지정 합니다.

`DUMP_FULLDUMP`\
전체 덤프를 크게 지정 합니다.

## <a name="remarks"></a>설명
[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) 메서드에 인수로 전달 됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)

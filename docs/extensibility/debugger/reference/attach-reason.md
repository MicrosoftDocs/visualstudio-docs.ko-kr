---
title: ATTACH_REASON | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca871d9dac2b6f37018af925eece5c1a6f3d1585
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738130"
---
# <a name="attach_reason"></a>ATTACH_REASON
디버그 엔진(DE)이 프로그램 노드에 연결되는 이유를 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_ATTACH_REASON {
    ATTACH_REASON_LAUNCH = 0x0001,
    ATTACH_REASON_USER   = 0x0002,
    ATTACH_REASON_AUTO   = 0x0003
};
typedef DWORD ATTACH_REASON;
```

```csharp
public enum enum_ATTACH_REASON {
    ATTACH_REASON_LAUNCH = 0x0001,
    ATTACH_REASON_USER   = 0x0002,
    ATTACH_REASON_AUTO   = 0x0003
};
```

## <a name="fields"></a>필드
`ATTACH_REASON_AUTO`\
프로세스가 현재 디버그 모드에 있기 때문에 연결합니다.

`ATTACH_REASON_LAUNCH`\
프로세스가 시작되었기 때문에 연결합니다.

`ATTACH_REASON_USER`\
사용자 요청으로 인해 연결합니다.

## <a name="remarks"></a>설명
이러한 값은 [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md) 및 [연결](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) 메서드의 매개 변수로 사용됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [연결](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)

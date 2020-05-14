---
title: PROCESS_INFO_FLAGS | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 36c4cbbe17a109eacd69b76500e8c10d21d2d554
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713958"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS

프로세스의 특성을 설명하거나 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
```

## <a name="fields"></a>필드

`PIFLAG_SYSTEM_PROCESS`\
프로세스가 시스템 프로세스임을 나타냅니다.

`PIFLAG_DEBUGGER_ATTACHED`\
프로세스가 디버거에 의해 디버깅되고 있음을 나타냅니다. 디버거일 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 수도, 아니면 다른 디버거일 수도 있습니다(예: WinDbg).

`PIFLAG_PROCESS_STOPPED`\
프로세스가 중지됨을 나타냅니다. 또한 지정된 `PIFLAG_DEBUGGER_ATTACHED` 경우에만 유효합니다. 비주얼 스튜디오 2005 이상에서 사용할 수 있습니다.

`PIFLAG_PROCESS_RUNNING`\
프로세스가 실행 중임을 나타냅니다. 또한 지정된 `PIFLAG_DEBUGGER_ATTACHED` 경우에만 유효합니다. 비주얼 스튜디오 2005 이상에서 사용할 수 있습니다.

## <a name="remarks"></a>설명

`Flags` [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) 구조의 부재에 사용됩니다.

이러한 플래그는 약간 으로 `OR`결합될 수 있습니다.

## <a name="requirements"></a>요구 사항

헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조

- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)

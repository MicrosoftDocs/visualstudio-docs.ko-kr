---
title: AD_PROCESS_ID_TYPE | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a88fbe97cede8d343f1a96bc1917a69b8905b02b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738193"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 구조에서 프로세스 ID를 해석하는 방법을 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
typedef DWORD AD_PROCESS_ID_TYPE;
```

```csharp
public enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
```

## <a name="fields"></a>필드
`AD_PROCESS_ID_SYSTEM`\
프로세스 ID는 시스템 식별자입니다. AD_PROCESS_ID `ProcessId.dwProcessId` 구조의 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 필드를 사용합니다.

`AD_PROCESS_ID_GUID`\
프로세스 ID는 GUID입니다. `AD_PROCESS_ID` 구조의 `ProcessId.guidProcessId` 필드를 사용합니다.

## <a name="remarks"></a>설명
`ProcessIdType` [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 구조체의 멤버에 사용되어 구조에 포함된 프로세스 ID의 유형을 식별합니다. 구조에서 공용 구조의 공용 구조조정을 `ProcessId` 해석하는 방법을 결정합니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)

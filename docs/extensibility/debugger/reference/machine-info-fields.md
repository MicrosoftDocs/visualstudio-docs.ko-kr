---
title: MACHINE_INFO_FIELDS | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89a2552bb6a8bea88f54a897b829ab89b30ff413
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714513"
---
# <a name="machine_info_fields"></a>MACHINE_INFO_FIELDS
특정 컴퓨터에 대해 검색할 정보의 종류를 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
typedef DWORD MACHINE_INFO_FIELDS;
```

```csharp
public enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
```

## <a name="fields"></a>필드
 `MCIF_NAME`\
 구조에서 `bstrName` 필드를 초기화/사용합니다.

 `MCIF_FLAGS`\
 구조에서 `Flags` 필드를 초기화/사용합니다.

 `MIF_ALL`\
 구조의 모든 필드를 초기화/사용합니다.

## <a name="remarks"></a>설명
 이러한 값은 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) 메서드에 전달되어 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) 구조의 구성원을 초기화할 구성원을 나타냅니다.

 또한 사용 `Fields` 되고 유효한 `MACHINE_INFO` 필드를 나타내는 구조의 멤버에 사용 됩니다.

 이러한 플래그는 약간 으로 `OR`결합될 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)

---
title: MACHINE_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FLAGS
helpviewer_keywords:
- MACHINE_INFO_FLAGS enumeration
ms.assetid: 1482095d-9a2e-4ef1-9e14-362c0b85194e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b74955d65ff34c4787de03c3b03383fe7eb702cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714508"
---
# <a name="machine_info_flags"></a>MACHINE_INFO_FLAGS
컴퓨터를 설명 하는 데 사용 됩니다.

## <a name="syntax"></a>Syntax

```cpp
enum enum_MACHINE_INFO_FLAGS { 
   MCIFLAG_TERMINAL_SERVICES_AVAILABLE = 0x00000001
};
typedef DWORD MACHINE_INFO_FLAGS;
```

```csharp
public enum enum_MACHINE_INFO_FLAGS { 
   MCIFLAG_TERMINAL_SERVICES_AVAILABLE = 0x00000001
};
```

## <a name="fields"></a>필드
 `MCIFLAG_TERMINAL_SERVICES_AVAILABLE`\
 터미널 서비스를 사용할 수 있음을 나타냅니다.

## <a name="remarks"></a>설명
 `Flags` [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) 구조체의 멤버로 사용 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)

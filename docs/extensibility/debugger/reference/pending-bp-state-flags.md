---
title: PENDING_BP_STATE_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_FLAGS
helpviewer_keywords:
- PENDING_BP_STATE_FLAGS enumeration
ms.assetid: 85522449-3fd8-4da5-b0fe-a43160e0c33b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f603b7a1660f9913ce10b2ecf07adb53f9279d48
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890008"
---
# <a name="pending_bp_state_flags"></a>PENDING_BP_STATE_FLAGS
보류 중인 중단점 상태 플래그를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_PENDING_BP_STATE_FLAGS { 
   PBPSF_NONE        = 0x0000,
   PBPSF_VIRTUALIZED = 0x0001
};
typedef DWORD PENDING_BP_STATE_FLAGS;
```

```csharp
public enum enum_PENDING_BP_STATE_FLAGS { 
   PBPSF_NONE        = 0x0000,
   PBPSF_VIRTUALIZED = 0x0001
};
```

## <a name="fields"></a>필드
 `PBPSF_NONE` Placeholder.

 `PBPSF_VIRTUALIZED` 새 코드를 로드할 때마다 바인딩되는 보류 중인 가상화 된 중단점을 지정 합니다.

## <a name="remarks"></a>설명
 `flags` [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) 구조체의 멤버에 사용 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)

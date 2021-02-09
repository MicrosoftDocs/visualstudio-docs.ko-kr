---
title: BP_RES_DATA_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RES_DATA_FLAGS
helpviewer_keywords:
- BP_RES_DATA_FLAGS enumeration
ms.assetid: d97611e2-def6-45a9-ad7d-eedf2ad4c82b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a90b8e9ffdc8009802c7e4c88927f69737eb83e4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901952"
---
# <a name="bp_res_data_flags"></a>BP_RES_DATA_FLAGS
데이터 중단점이 하드웨어에서 에뮬레이션 되는지 또는 구현 되는지 여부를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_BP_RES_DATA_FLAGS {
    BP_RES_DATA_EMULATED = 0x0001
};
typedef DWORD BP_RES_DATA_FLAGS;
```

```csharp
public enum enum_BP_RES_DATA_FLAGS {
    BP_RES_DATA_EMULATED = 0x0001
};
```

## <a name="fields"></a>필드
`BP_RES_DATA_EMULATED`\
데이터 중단점을 에뮬레이션 하도록 지정 합니다.

## <a name="remarks"></a>설명
`dwFlags` [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) 구조체의 멤버에 사용 됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)

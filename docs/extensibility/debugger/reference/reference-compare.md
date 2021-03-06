---
description: 참조에 대 한 비교 유형을 지정 합니다.
title: REFERENCE_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- REFERENCE_COMPARE
helpviewer_keywords:
- REFERENCE_COMPARE enumeration
ms.assetid: e31cdc78-f621-498b-9ca4-aefa790b9f6f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 65b38d342dc84e680e202b73976550fcca5809cf
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221953"
---
# <a name="reference_compare"></a>REFERENCE_COMPARE
참조에 대 한 비교 유형을 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_REFERENCE_COMPARE { 
   REF_COMPARE_EQUAL        = 0x0001,
   REF_COMPARE_LESS_THAN    = 0x0002,
   REF_COMPARE_GREATER_THAN = 0x0003
};
typedef DWORD REFERENCE_COMPARE;
```

```csharp
public enum enum_REFERENCE_COMPARE { 
   REF_COMPARE_EQUAL        = 0x0001,
   REF_COMPARE_LESS_THAN    = 0x0002,
   REF_COMPARE_GREATER_THAN = 0x0003
};
```

## <a name="fields"></a>필드
 `REF_COMPARE_EQUAL`\
 같음 비교를 지정 합니다.

 `REF_COMPARE_LESS_THAN`\
 보다 작음 비교를 지정 합니다.

 `REF_COMPARE_GREATER_THAN`\
 보다 큼 비교를 지정 합니다.

## <a name="remarks"></a>설명
 [Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md) 메서드에 인수로 전달 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [비교](../../../extensibility/debugger/reference/idebugreference2-compare.md)

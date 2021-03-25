---
description: IDebugField 개체에서 가져오고 사용자에 게 표시할 정보의 종류를 나타내는 유효한 값을 열거 합니다.
title: DisplayKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayKind enumeration
ms.assetid: 940968c5-6065-4bda-8ee6-c31597db4d71
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b8c474c9295ceedbdffd286e99975c375ea69fc4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096033"
---
# <a name="displaykind"></a>DisplayKind
[Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 개체에서 가져오고 사용자에 게 표시할 정보의 종류를 나타내는 유효한 값을 열거 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_DisplayKind
{
    DisplayKind_Value = 0x1,
    DisplayKind_Name = 0x2,
    DisplayKind_Type = 0x3,
};
typedef DWORD DisplayKind;
```

```csharp
public enum enum_DisplayKind
{
    DisplayKind_Value = 0x1,
    DisplayKind_Name = 0x2,
    DisplayKind_Type = 0x3,
};
```

## <a name="fields"></a>필드
`DisplayKind_Value`\
필드의 값입니다.

`DisplayKind_Name`\
필드의 이름입니다.

`DisplayKind_Type`\
필드의 유형입니다.

## <a name="requirements"></a>요구 사항
헤더: Ee. h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)

---
description: 모듈의 기호 상태를 지정 합니다.
title: MODULE_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FLAGS
helpviewer_keywords:
- MODULE_INFO_FLAGS enumeration
ms.assetid: e22d3723-b4d4-4524-8a2f-3adb55bbd273
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bfe1639ea187c6f03327a2278aaa9f849309a2af
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079711"
---
# <a name="module_info_flags"></a>MODULE_INFO_FLAGS
모듈의 기호 상태를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_MODULE_INFO_FLAGS {
   MIF_SYMBOLS_LOADED = 0x0001
};
typedef DWORD MODULE_INFO_FLAGS;
```

```csharp
public enum enum_MODULE_INFO_FLAGS {
   MIF_SYMBOLS_LOADED = 0x0001
};
```

## <a name="fields"></a>필드
 `MIF_SYMBOLS_LOADED`\
 모듈에서 하나 이상의 기호 집합을 로드 했습니다 (그렇지 않으면 기호가 로드 되지 않음).

## <a name="remarks"></a>설명
 이 값은 [Get기호 Searchinfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) 메서드에 의해 반환 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)

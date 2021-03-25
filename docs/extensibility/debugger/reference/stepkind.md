---
description: 단계별 실행 단계 종류를 지정 합니다.
title: STKIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- STEPKIND
helpviewer_keywords:
- STEPKIND enumeration
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2363062ba8de362980a490133b77e374e9bc8507
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061500"
---
# <a name="stepkind"></a>STEPKIND
단계별 실행 단계 종류를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
typedef DWORD STEPKIND;
```

```csharp
public enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
```

## <a name="fields"></a>필드
 `STEP_INTO`\
 한 단계씩 함수를 수행 합니다.

 `STEP_OVER`\
 함수에 대 한 단계를 수행 합니다.

 `STEP_OUT`\
 함수에서 작업을 수행 합니다.

 `STEP_BACKWARDS`\
 함수를 한 단계씩 뒤로 이동 합니다.

## <a name="remarks"></a>설명
 [단계](../../../extensibility/debugger/reference/idebugprocess3-step.md) 메서드에 인수로 전달 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)

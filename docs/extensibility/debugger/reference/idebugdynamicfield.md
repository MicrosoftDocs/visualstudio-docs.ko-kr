---
description: 이 인터페이스는 변수의 형식을 나타냅니다.
title: IDebugDynamicField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bf1d72bfa38e6af0419e696b267699d10340cc68
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094083"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
이 인터페이스는 변수의 형식을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 이 인터페이스는 런타임에 결정 될 수 있는 모든 형식에 대 한 기본 클래스로 기호 공급자에 의해 구현 됩니다. 이는 관리 코드에만 해당 됩니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 이 인터페이스는 더 특수화 된 인터페이스가 파생 될 수 있는 기본 클래스를 나타냅니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는에서 상속 된 메서드 이외의 메서드를 제공 하지 않습니다 `IDebugField` .

## <a name="requirements"></a>요구 사항
 헤더: sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

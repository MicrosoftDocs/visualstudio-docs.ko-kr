---
title: 이데버그 다이내믹필드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15f0ddf70849377d37ec74839550de6057b3450c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731320"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
이 인터페이스는 변수의 형식을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 이 인터페이스는 런타임에 결정할 수 있는 모든 형식에 대한 기본 클래스로 심볼 공급자에 의해 구현됩니다. 이는 관리 되는 코드에 만 해당 됩니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스는 보다 특수화된 인터페이스를 파생시킬 수 있는 기본 클래스를 나타냅니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 에서 상속된 메서드 이외의 `IDebugField`메서드를 제공하지 않습니다.

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

---
description: IDebugBinder 개체의 동적 필드를 나타냅니다.
title: IDebugDynamicFieldCOMPlus | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus interface
ms.assetid: c3a25f27-327a-4bdb-b026-27d436ddcd0c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f365bcadba5349ae43e1b75683ec100fdabbf338
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094018"
---
# <a name="idebugdynamicfieldcomplus"></a>IDebugDynamicFieldCOMPlus
[Idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md) 개체의 동적 필드를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugDynamicFieldCOMPlus : IDebugDynamicField
```

## <a name="methods"></a>메서드
 [Idebugdynamicfield](../../../extensibility/debugger/reference/idebugdynamicfield.md) 인터페이스의 메서드 외에도이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|Description|
|------------|-----------------|
|[GetTypeFromPrimitive](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromprimitive.md)|기본 형식이 지정 된 형식을 검색 합니다.|
|[GetTypeFromTypeDef](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromtypedef.md)|해당 토큰이 지정 된 형식을 검색 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

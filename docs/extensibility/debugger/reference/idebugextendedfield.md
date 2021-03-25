---
description: 관리 코드 제네릭을 지 원하는 데 사용할 수 있는 필드 형식을 확장 합니다.
title: IDebugExtendedField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d8214703fb1ffc05d3f58f8348870a8505cc8f59
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077189"
---
# <a name="idebugextendedfield"></a>IDebugExtendedField
관리 코드 제네릭을 지 원하는 데 사용할 수 있는 필드 형식을 확장 합니다.

## <a name="syntax"></a>구문

```
IDebugExtendedField : IDebugField
```

## <a name="methods"></a>메서드
 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스의 메서드 외에도이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|Description|
|------------|-----------------|
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|지정 된 확장 필드 종류를 검색 합니다.|
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|필드가 폐쇄형 형식을 나타내는지 여부를 확인 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

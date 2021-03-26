---
description: 배열 형식을 만들 수 있도록 IDebugTypeFieldBuilder를 확장 합니다.
title: IDebugTypeFieldBuilder2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48bdc4f1bb2668b83da3b042df194e73045e45fc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083520"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
배열 형식을 만들 수 있도록 **Idebugtypefieldbuilder** 를 확장 합니다.

## <a name="syntax"></a>구문

```
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder
```

## <a name="notes-for-callers"></a>호출자 참고 사항
 이 인터페이스는 기호 공급자에서 가져올 수 있습니다.

## <a name="methods"></a>메서드
 [Idebugtypefieldbuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) 인터페이스의 메서드 외에도이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|Description|
|------------|-----------------|
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|지정 된 형식 및 크기의 배열을 만듭니다.|

## <a name="requirements"></a>요구 사항
 헤더: Sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

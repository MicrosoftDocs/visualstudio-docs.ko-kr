---
description: Debug 선택적 한정자를 나타냅니다.
title: IDebugModOpt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ffb235d58c254d130636da0f4b97961c11f9a372
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087901"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Debug 선택적 한정자를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>호출자 참고 사항
 클래스 또는 메서드를 나타내는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 개체에서 가져옵니다.

## <a name="methods"></a>메서드
 이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|Description|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|선택적 한정자 목록을 검색 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

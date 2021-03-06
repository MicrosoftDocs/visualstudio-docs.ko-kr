---
description: 형식을 나타내는 필드를 만드는 기능을 나타냅니다.
title: IDebugTypeFieldBuilder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1bc4f58470792cac8bdb68ede4ddf37567bac208
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223110"
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
형식을 나타내는 필드를 만드는 기능을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugTypeFieldBuilder : IUnknown
```

## <a name="notes-for-callers"></a>호출자 참고 사항
 이 인터페이스는 기호 공급자에서 가져옵니다.

## <a name="methods"></a>메서드
 이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|기본 형식을 나타내는 개체를 만듭니다.|
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|지정 된 형식에 대 한 포인터를 만듭니다.|

## <a name="requirements"></a>요구 사항
 헤더: Sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

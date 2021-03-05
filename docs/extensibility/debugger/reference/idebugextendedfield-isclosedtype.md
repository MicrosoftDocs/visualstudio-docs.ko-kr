---
description: 필드가 폐쇄형 형식을 나타내는지 여부를 확인 합니다.
title: 'IDebugExtendedField:: IsClosedType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4f13fa0f143ac6adb8fb3493621b7ef638a394ca
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152119"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
필드가 폐쇄형 형식을 나타내는지 여부를 확인 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT IsClosedType(
   void
);
```

```csharp
int IsClosedType();
```

## <a name="return-value"></a>Return Value
 필드가 닫힌 형식이 면는를 반환 하 `S_OK` 고, 그렇지 않으면를 반환 `S_FALSE` 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)

---
title: 'IDebugExtendedField:: IsClosedType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4524d7c899480518e669f1f77a4756a83e0cf52f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729057"
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

## <a name="see-also"></a>추가 정보
- [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)

---
description: 지정 된 확장 필드 종류를 검색 합니다.
title: 'IDebugExtendedField:: GetExtendedKind | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField::GetExtendedKind
- GetExtendedKind
ms.assetid: 20dc1c13-3cc0-4bb4-9c99-fa85587c86c3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 334ed7f44c4b4c119a204af17a00b8329410d05e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152132"
---
# <a name="idebugextendedfieldgetextendedkind"></a>IDebugExtendedField::GetExtendedKind
지정 된 확장 필드 종류를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetExtendedKind(
   FIELD_KIND_EX* pdwKind
);
```

```csharp
int GetExtendedKind(
   ref enum_FIELD_KIND_EX pdwKind
);
```

## <a name="parameters"></a>매개 변수
`pdwKind`\
[in, out] 필드의 종류를 정의 하는 [FIELD_KIND_EX](../../../extensibility/debugger/reference/field-kind-ex.md) 열거형의 값입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)

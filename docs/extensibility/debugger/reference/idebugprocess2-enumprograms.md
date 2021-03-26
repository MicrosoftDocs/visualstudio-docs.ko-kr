---
description: 이 프로세스에 포함 된 모든 프로그램의 목록을 검색 합니다.
title: 'IDebugProcess2:: EnumPrograms | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumPrograms
helpviewer_keywords:
- IDebugProcess2::EnumPrograms
ms.assetid: f5b7295d-487d-464f-a4c6-d54175b07705
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1967415ba70e28f19bc251297ada07ea430a3202
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071651"
---
# <a name="idebugprocess2enumprograms"></a>IDebugProcess2::EnumPrograms
이 프로세스에 포함 된 모든 프로그램의 목록을 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumPrograms( 
   IEnumDebugPrograms2** ppEnum
);
```

```csharp
int EnumPrograms( 
   out IEnumDebugPrograms2 ppEnum
);
```

## <a name="parameters"></a>매개 변수
`ppEnum`\
제한이 프로세스의 모든 프로그램 목록을 포함 하는 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참조
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)

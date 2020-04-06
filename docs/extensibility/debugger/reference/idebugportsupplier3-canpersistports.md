---
title: IDebugPortSupplier3::캔지속포트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2bf436d788b517300bee9a13b66b0ca3747bcc43
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724469"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
이 메서드는 포트 공급자가 디버거 호출 간에 포트를 디스크에 기록하여 포트를 지속할 수 있는지 여부를 결정합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>매개 변수
 없음

## <a name="return-value"></a>Return Value
 `S_OK`포트를 `S_FALSE` 유지하거나 포트를 유지할 수 없음을 나타낼 수 있습니다.

## <a name="remarks"></a>설명
 포트 공급자가 포트를 지속할 수 있는 경우 포트가 소멸될 때 포트를 유지한 다음 다시 인스턴스화될 때 다시 로드해야 합니다.

## <a name="see-also"></a>참조
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)

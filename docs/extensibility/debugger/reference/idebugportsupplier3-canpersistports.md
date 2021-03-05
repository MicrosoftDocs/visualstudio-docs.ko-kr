---
description: 이 메서드는 포트 공급자가 디버거 호출 사이에 포트를 디스크에 기록 하 여 유지할 수 있는지 여부를 결정 합니다.
title: 'IDebugPortSupplier3:: CanPersistPorts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 092f6e372d8f98e731ad90a7d261fe015d019656
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172011"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
이 메서드는 포트 공급자가 디버거 호출 사이에 포트를 디스크에 기록 하 여 유지할 수 있는지 여부를 결정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>매개 변수
 없음

## <a name="return-value"></a>반환 값
 `S_OK` 포트가 지속 될 수 있으면이 고, `S_FALSE` 포트를 지속할 수 없음을 나타내려면입니다.

## <a name="remarks"></a>설명
 포트 공급자가 포트를 유지할 수 있는 경우 해당 포트는 제거 될 때이를 수행 하 고 다시 인스턴스화될 때 다시 로드 해야 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)

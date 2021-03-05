---
description: 이 메서드는 필드의 컨테이너를 가져옵니다.
title: 'IDebugField:: GetContainer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetContainer
helpviewer_keywords:
- IDebugField::GetContainer method
ms.assetid: 6d6c8213-6181-4adf-9584-3e4cac163dd8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 39be9de82e6356b16562ca4b45ea67bb40e3764f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152002"
---
# <a name="idebugfieldgetcontainer"></a>IDebugField::GetContainer
이 메서드는 필드의 컨테이너를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetContainer( 
   IDebugContainerField** ppContainerField
);
```

```csharp
int GetContainer(
   out IDebugContainerField ppContainerField
);
```

## <a name="parameters"></a>매개 변수
`ppContainerField`\
제한이 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스가 나타내는 컨테이너를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 필드에 컨테이너가 없는 경우 반환 되는은 `ppContainerField` null 값입니다.

## <a name="see-also"></a>참고 항목
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)

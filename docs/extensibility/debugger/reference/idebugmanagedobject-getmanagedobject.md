---
description: 관리 되는 개체를 나타내는 인터페이스를 반환 합니다.
title: 'IDebugManagedObject:: GetManagedObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1a262759cfcedd5fb0d09bcb995dcbcb7f7ee2a7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165269"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
관리 되는 개체를 나타내는 인터페이스를 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetManagedObject( 
   IUnknown** ppManagedObject
);
```

```cpp
int GetManagedObject(
   out object ppManagedObject
);
```

## <a name="parameters"></a>매개 변수
`ppManagedObject`\
제한이 관리 되는 개체를 나타내는 인터페이스를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드에서 반환 된 인터페이스는 해당 메서드가 호출 될 수 있도록 관리 되는 클래스에서 구현 하는 인터페이스에 대해 쿼리할 수 있습니다.

## <a name="see-also"></a>참고 항목
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)

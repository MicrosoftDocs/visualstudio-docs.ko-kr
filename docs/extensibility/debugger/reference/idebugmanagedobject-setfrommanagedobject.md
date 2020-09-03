---
title: 'IDebugManagedObject:: SetFromManagedObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4056befa0b5b053d480983901b24feb6b25cf538
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727705"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
매개 변수로 제공 된 값 클래스의 인스턴스에서 값 클래스 개체의 인스턴스 값을 설정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetFromManagedObject( 
   IUnknown* pManagedObject
);
```

```csharp
int SetFromManagedObject(
   object pManagedObject
);
```

## <a name="parameters"></a>매개 변수
`pManagedObject`\
진행 새 값을 포함 하는 관리 되는 개체를 나타내는 인터페이스입니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드는 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) 개체가 나타내는 관리 되는 개체를 변경 하는 데 사용 됩니다.

## <a name="see-also"></a>추가 정보
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)

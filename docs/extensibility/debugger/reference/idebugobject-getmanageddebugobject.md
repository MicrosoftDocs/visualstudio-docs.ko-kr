---
title: 아이디버그 오브젝트::GetManaged디버그오브젝트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67d0d7a8642c9dd90067b0e197f420d4cc821faa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726682"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
디버그 엔진의 주소 공간에 관리되는 개체의 복사본을 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetManagedDebugObject( 
   IDebugManagedObject** ppObject
);
```

```csharp
int GetManagedDebugObject(
   out IDebugManagedObject ppObject
);
```

## <a name="parameters"></a>매개 변수
`ppObject`\
【아웃】 새로 생성된 관리 개체를 나타내는 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다. 이 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 관리 되는 값 클래스 인스턴스를 나타내지 않는 경우 E_FAIL 반환 합니다.

## <a name="remarks"></a>설명
 이 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 개체는 인스턴스와 같은 관리되는 `System.Decimal` 값 클래스 인스턴스를 나타내야 합니다. 로컬 복사본을 사용하여 [평가](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) 호출의 오버헤드가 제거됩니다.

## <a name="see-also"></a>참조
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)

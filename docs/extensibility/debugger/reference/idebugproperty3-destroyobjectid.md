---
title: IDebugProperty3::D estroyObjectID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6afc0f5243d9f50f2d777c0bd43e6bba1de5e495
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936108"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
이 속성에 연결 된 고유 ID를 소멸 시킵니다 .이는 호출자가이 속성을 다른 모든 속성에서 고유 하 게 식별 하는 데 더 이상 관심이 없음을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
HRESULT DestroyObjectID(
   void
);
```

```csharp
int DestroyObjectID();
```

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 디버그 엔진이 속성의 고유 Id를 지원할 필요가 없는 경우 (이미 고유 하 게 내부적으로 추적 하기 때문에)이 메서드에 대해를 반환 하기만 하면 됩니다 `E_NOTIMPL` .

 호출자가이 속성이 다른 모든 속성에서 고유 하 게 식별 되는지 확인 하려는 경우 [Createobjectid](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) 메서드를 호출 하 여 고유한 id를 만듭니다.

## <a name="see-also"></a>참고 항목
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)

---
title: 'IDebugFunctionObject:: CreateStringObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateStringObject
helpviewer_keywords:
- IDebugFunctionObject::CreateStringObject method
ms.assetid: fd6070ab-07d4-4ea1-8d71-b16592d6f1a7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f1fe290655781dd144e7c7b3951e021124e46086
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929955"
---
# <a name="idebugfunctionobjectcreatestringobject"></a>IDebugFunctionObject::CreateStringObject
문자열 개체를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CreateStringObject( 
   LPCOLESTR      pcstrString,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObject(
   string      pcstrString,
   out IDebugObject ppOjbect
);
```

## <a name="parameters"></a>매개 변수
`pcstrString`\
진행 문자열 개체의 문자열 값입니다.

`ppObject`\
제한이 새로 만든 string 개체를 나타내는 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 개체를 반환 합니다.

## <a name="return-value"></a>Return Value
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 [Idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 인터페이스로 표현 되는 함수에 대 한 매개 변수인 문자열을 나타내는 개체를 만들려면이 메서드를 호출 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)

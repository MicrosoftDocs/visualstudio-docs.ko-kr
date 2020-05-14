---
title: IDebugFunctionObject::생성 스트링오브젝트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateStringObject
helpviewer_keywords:
- IDebugFunctionObject::CreateStringObject method
ms.assetid: fd6070ab-07d4-4ea1-8d71-b16592d6f1a7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 40a13b9b388caa6a1ae6e3e470e4ea02553fa0ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728521"
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
【인】 문자열 개체의 문자열 값입니다.

`ppObject`\
【아웃】 새로 만든 문자열 개체를 나타내는 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 개체를 반환 합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 인터페이스에 의해 표현 되는 함수에 대 한 매개 변수는 문자열을 나타내는 개체를 만드는이 메서드를 호출 합니다.

## <a name="see-also"></a>참조
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)

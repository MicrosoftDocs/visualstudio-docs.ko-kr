---
description: 생성자를 사용 하 여 개체를 만듭니다.
title: 'IDebugFunctionObject:: CreateObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27608634859ae96a8fb9461076397bb6df53570d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073562"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
생성자를 사용 하 여 개체를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CreateObject( 
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject(
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   out IDebugObject     ppObject
);
```

## <a name="parameters"></a>매개 변수
`pConstructor`\
진행 만들 개체의 생성자를 나타내는 [Idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 개체입니다.

`dwArgs`\
진행 배열에 있는 매개 변수의 수 `pArg` 입니다. 생성자에 전달 된 매개 변수 수를 나타냅니다.

`pArg`\
진행 생성자에 전달 된 매개 변수를 나타내는 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 개체의 배열입니다.

`ppObject`\
제한이 `IDebugObject` 새로 만든 개체를 나타내는을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 [Idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 인터페이스로 표현 되는 함수에 대 한 매개 변수인 클래스 (또는 생성자가 필요한 다른 복합 형식)의 인스턴스를 나타내는 개체를 만들려면이 메서드를 호출 합니다.

 개체 매개 변수에 생성자가 필요 하지 않은 경우 [Createobjectnoconstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) 메서드를 호출 합니다.

## <a name="see-also"></a>참조
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)

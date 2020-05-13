---
title: IDebugFunctionObject2::오브젝트 만들기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6de1a30a032919a90fbb3d760837d5eeca00feaf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728483"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
지정된 평가 플래그 설정 및 시간 지정 값을 사용하는 개체를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CreateObject (
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject (
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   out IDebugObject**   ppObject
);
```

## <a name="parameters"></a>매개 변수
`pConstructor`\
【인】 생성할 개체의 생성자임을 나타내는 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 개체입니다.

`dwArgs`\
【인】 배열의 매개 변수 `pArg` 수입니다. 생성자에게 전달된 매개 변수 수를 나타냅니다.

`pArgs`\
【인】 생성자에게 전달된 매개 변수를 나타내는 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 개체의 배열입니다.

`dwEvalFlags`\
【인】 평가를 수행할 방법을 지정하는 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 열거형의 플래그 조합입니다.

`dwTimeout`\
【인】 이 메서드에서 반환하기 전에 기다릴 수 있는 최대 시간(밀리초)입니다. **무한을** 사용하여 무기한 기다립니다.

`ppObject`\
【아웃】 새로 만든 개체를 나타내는 **IDebugObject를** 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드를 호출하여 클래스의 인스턴스또는 생성자가 필요한 다른 복잡한 형식의 매개 변수를 나타내는 개체를 만듭니다.

## <a name="see-also"></a>참조
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)

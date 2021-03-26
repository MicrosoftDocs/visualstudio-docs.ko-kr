---
description: 지정 된 계산 플래그 설정 및 시간 제한 값을 사용 하는 개체를 만듭니다.
title: 'IDebugFunctionObject2:: CreateObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b75cd2fae72d0ce8901445c3271a955100391d75
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063567"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
지정 된 계산 플래그 설정 및 시간 제한 값을 사용 하는 개체를 만듭니다.

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
진행 만들 개체의 생성자를 나타내는 [Idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 개체입니다.

`dwArgs`\
진행 배열에 있는 매개 변수의 수 `pArg` 입니다. 생성자에 전달 된 매개 변수 수를 나타냅니다.

`pArgs`\
진행 생성자에 전달 된 매개 변수를 나타내는 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 개체의 배열입니다.

`dwEvalFlags`\
진행 계산을 수행 하는 방법을 지정 하는 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 열거형의 플래그 조합입니다.

`dwTimeout`\
진행 이 메서드에서 반환 될 때까지 대기 하는 최대 시간 (밀리초)입니다. 무기한 **대기 하려면 무기한** 을 사용 합니다.

`ppObject`\
제한이 새로 만든 개체를 나타내는 **Idebugobject** 를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드를 호출 하 여 클래스의 인스턴스 또는 생성자를 필요로 하는 기타 복합 형식 (매개 변수)을 나타내는 개체를 만듭니다.

## <a name="see-also"></a>참조
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)

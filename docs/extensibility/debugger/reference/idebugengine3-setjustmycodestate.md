---
description: 이 메서드는 디버그 엔진에 JustMyCode 상태 정보를 알려 줍니다.
title: 'IDebugEngine3:: SetJustMyCodeState | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e527dbaeb9c04171bf26ea00e550eac336ac6a8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066125"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
이 메서드는 디버그 엔진에 JustMyCode 상태 정보를 알려 줍니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
);
```

```csharp
int SetJustMyCodeState(
   int             fUpdate,
   uint            dwModules,
   JMC_CODE_SPEC[] rgJMCSpec
);
```

## <a name="parameters"></a>매개 변수
`fUpdate`\
진행 `TRUE`현재 정보를 업데이트 하는 0이 아닌 (), `FALSE` 모든 정보를 다시 설정 (이전에 설정한 것은 무시 함)

`dwModules`\
진행 다음의 정보 구조 수 `rgJMCSpec.`

`rgJMCSpec`\
진행 사용할 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) 구조체의 배열입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 JustMyCode는 해당 시스템 코드에 대해 소스 코드를 사용할 수 있는 경우에도 사용자에 게 속하는 코드와 시스템 코드와 같은 모든 중간 코드를 무시 하는 것을 디버깅 하는 개념입니다.

## <a name="see-also"></a>참조
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)

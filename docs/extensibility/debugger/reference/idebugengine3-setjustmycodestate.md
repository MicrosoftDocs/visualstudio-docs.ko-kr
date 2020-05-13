---
title: 아이데버그엔진3::세트저스마이코드스테이트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9930f8ecf0c2f9b6fff4ce1c9e3edb935c5a7912
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730678"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
이 메서드는 디버그 엔진에 JustMyCode 상태 정보에 대해 알려줍니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
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
【인】 Nonzero`TRUE`() 현재 정보를 업데이트하려면, 0 ()`FALSE`모든 정보를 재설정 (이전에 설정 된 아무것도 무시).

`dwModules`\
【인】 정보 구조의 수`rgJMCSpec.`

`rgJMCSpec`\
【인】 사용할 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) 구조의 배열입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 JustMyCode는 사용자에게 속한 코드만 디버깅하고 해당 시스템 코드에 대해 소스 코드를 사용할 수 있는 경우에도 시스템 코드와 같은 모든 중간 코드를 무시하는 개념입니다.

## <a name="see-also"></a>참조
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)

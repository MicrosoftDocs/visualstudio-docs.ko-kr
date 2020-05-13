---
title: 아이디버그스택프레임2::겟디버그퍼퍼피티 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetDebugProperty
helpviewer_keywords:
- IDebugStackFrame2::GetDebugProperty
ms.assetid: 02c2fa04-1424-4bca-9936-feaecd2afab6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aa98107ada265d232647d27b4050b507d4581df7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719790"
---
# <a name="idebugstackframe2getdebugproperty"></a>IDebugStackFrame2::GetDebugProperty
스택 프레임의 속성에 대한 설명을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetDebugProperty ( 
   IDebugProperty2** ppDebugProp
);
```

```csharp
int GetDebugProperty ( 
   out IDebugProperty2 ppDebugProp
);
```

## <a name="parameters"></a>매개 변수
`ppDebugProp`\
【아웃】 이 스택 프레임의 속성을 설명하는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 적절한 필터를 사용하여 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 메서드를 호출하면 스택 프레임과 연결된 로컬 변수, 메서드 매개 변수, 레지스터 및 "this" 포인터를 검색할 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

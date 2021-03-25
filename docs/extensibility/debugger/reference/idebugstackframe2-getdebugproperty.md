---
description: 스택 프레임의 속성에 대 한 설명을 가져옵니다.
title: 'IDebugStackFrame2:: GetDebugProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetDebugProperty
helpviewer_keywords:
- IDebugStackFrame2::GetDebugProperty
ms.assetid: 02c2fa04-1424-4bca-9936-feaecd2afab6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5c4017e5a14619c2ab5e3f98de65d7d2295e8586
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053479"
---
# <a name="idebugstackframe2getdebugproperty"></a>IDebugStackFrame2::GetDebugProperty
스택 프레임의 속성에 대 한 설명을 가져옵니다.

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
제한이 이 스택 프레임의 속성을 설명 하는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 적절 한 필터를 사용 하 여 [Enumchildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 메서드를 호출 하면 스택 프레임과 연결 된 지역 변수, 메서드 매개 변수, 레지스터 및 "this" 포인터를 검색할 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

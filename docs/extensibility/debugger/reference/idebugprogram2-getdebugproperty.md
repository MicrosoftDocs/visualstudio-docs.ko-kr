---
title: 아이디버그프로그램2::겟디버그프로퍼티 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33bc10aadf25eb95414cc5fd334c572b2f270429
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722886"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
프로그램의 속성을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetDebugProperty( 
   IDebugProperty2** ppProperty
);
```

```csharp
int GetDebugProperty( 
   out IDebugProperty2 ppProperty
);
```

## <a name="parameters"></a>매개 변수
`ppProperty`\
【아웃】 프로그램의 속성을 나타내는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드에서 반환되는 속성은 프로그램에 만 해당합니다. 프로그램이 두 개 이상의 속성을 반환해야 하는 경우 이 메서드에서 반환되는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 개체는 추가 속성의 컨테이너이며 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 메서드를 호출하면 모든 속성 목록이 반환됩니다.

 프로그램은 `IDebugProperty2` 인터페이스를 통해 설명할 수 있는 추가 속성의 수와 유형을 노출할 수 있습니다. IDE는 일반 속성 브라우저 사용자 인터페이스를 통해 추가 프로그램 속성을 표시할 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)

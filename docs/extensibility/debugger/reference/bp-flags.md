---
title: BP_FLAGS | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62626ff75a4545d89835d3136649191004291f8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738068"
---
# <a name="bp_flags"></a>BP_FLAGS
중단점을 설정할 때 추가 정보를 지정하는 데 사용할 수 있는 선택적 플래그를 제공합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
typedef DWORD BP_FLAGS;
```

```csharp
public enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
```

## <a name="fields"></a>필드
`BP_FLAG_NONE`\
중단점 플래그를 지정하지 않습니다.

`BP_FLAG_MAP_DOCPOSITION`\
디버그 엔진(DE)이 문서 위치를 사용하여 중단점을 매핑해야 한다고 지정합니다. 이는 ASP(활성 서버 페이지)와 같은 스크립트 지향 소스 파일에 설정된 중단점에만 적용됩니다.

`BP_FLAG_DONT_STOP`\
디버그 엔진에서 중단점을 처리해야 하지만 디버그 엔진이 궁극적으로 거기서 멈추지 않도록 지정합니다(즉, [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) 이벤트 개체는 전송되지 않아야 합니다). 이 플래그는 주로 추적점에서 사용되도록 설계되었습니다.

## <a name="remarks"></a>설명
[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 및 `dwFlags` [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 구조의 부재에 사용됩니다.

이러한 값은 약간 과 `OR`결합될 수 있습니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)

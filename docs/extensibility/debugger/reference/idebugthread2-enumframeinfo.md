---
title: 아이디버그스레드2::에넘프레임정보 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8bd3c6d46a577930cc7a2b87c85cd82a55f8cf66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718847"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
이 스레드의 스택 프레임 목록을 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumFrameInfo ( 
   FRAMEINFO_FLAGS        dwFieldSpec,
   UINT                   nRadix,
   IEnumDebugFrameInfo2** ppEnum
);
```

```csharp
int EnumFrameInfo ( 
   enum_FRAMEINFO_FLAGS     dwFieldSpec,
   uint                     nRadix,
   out IEnumDebugFrameInfo2 ppEnum
);
```

## <a name="parameters"></a>매개 변수
`dwFieldSpec`\
【인】 [frameINFO](../../../extensibility/debugger/reference/frameinfo.md) 구조체의 필드를 채울 지 지정하는 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) 열거형의 플래그 조합입니다. 함수 `FIF_FUNCNAME_FORMAT` 이름을 단일 문자열로 포맷할 플래그를 지정합니다.

`nRadix`\
【인】 Radix는 열거체에서 숫자 정보를 서식지정하는 데 사용됩니다.

`ppEnum`\
【아웃】 스택 프레임을 설명하는 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 구조 목록이 포함된 [IEnumDebugFrameFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 스레드의 프레임은 순서대로 위대해지며, 현재 프레임은 먼저 예류가 되고 가장 오래된 프레임은 마지막으로 수거됩니다.

## <a name="see-also"></a>참조
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)

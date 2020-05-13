---
title: 아이디버그스택프레임2::겟정보 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetInfo
helpviewer_keywords:
- IDebugStackFrame2::GetInfo
ms.assetid: 19c6870b-b94e-453c-bf19-82ce95b79d26
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 09768fc58640d79a3b5628bafc16b2267f1f8a4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719715"
---
# <a name="idebugstackframe2getinfo"></a>IDebugStackFrame2::GetInfo
스택 프레임에 대한 설명을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetInfo ( 
   FRAMEINFO_FLAGS dwFieldSpec,
   UINT            nRadix,
   FRAMEINFO*      pFrameInfo
);
```

```csharp
int GetInfo ( 
   enum_FRAMEINFO_FLAGS dwFieldSpec,
   uint                 nRadix,
   FRAMEINFO[]          pFrameInfo
);
```

## <a name="parameters"></a>매개 변수
`dwFieldSpec`\
【인】 매개 변수의 필드를 채울 FRAMEINFO_FLAGS 필드를 지정하는 [플래그의](../../../extensibility/debugger/reference/frameinfo-flags.md) `pFrameInfo` 조합입니다.

`nRadix`\
【인】 숫자 정보를 서식 지정하는 데 사용할 radix입니다.

`pFrameInfo`\
【아웃】 스택 프레임에 대한 설명으로 채워진 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 구조입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)

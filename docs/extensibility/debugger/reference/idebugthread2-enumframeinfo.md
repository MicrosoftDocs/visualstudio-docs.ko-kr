---
title: 'IDebugThread2:: Enum프레임 정보 | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718847"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
이 스레드에 대 한 스택 프레임 목록을 검색 합니다.

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
진행 작성할 [프레임 정보](../../../extensibility/debugger/reference/frameinfo.md) 구조의 필드를 지정 하는 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) 열거형의 플래그 조합입니다. `FIF_FUNCNAME_FORMAT`함수 이름을 단일 문자열로 지정 하는 플래그를 지정 합니다.

`nRadix`\
진행 열거자의 숫자 정보에 서식을 지정 하는 데 사용 되는 기 하 합니다.

`ppEnum`\
제한이 스택 프레임을 설명 하는 [프레임 정보](../../../extensibility/debugger/reference/frameinfo.md) 구조 목록을 포함 하는 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 스레드의 프레임은 순서 대로 열거 됩니다. 현재 프레임이 먼저 열거 되 고 가장 오래 된 프레임이 마지막으로 열거 됩니다.

## <a name="see-also"></a>추가 정보
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)

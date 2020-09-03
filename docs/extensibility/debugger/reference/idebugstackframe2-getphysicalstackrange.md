---
title: 'IDebugStackFrame2:: Get Stackrange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3df924c6c8a4373082d61575e4ad8a7ec3f161d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719662"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
스택 프레임과 연결 된 실제 주소 범위의 컴퓨터 종속 표현을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetPhysicalStackRange ( 
   UINT64* paddrMin,
   UINT64* paddrMax
);
```

```csharp
int GetPhysicalStackRange ( 
   out ulong paddrMin,
   out ulong paddrMax
);
```

## <a name="parameters"></a>매개 변수
`paddrMin`\
제한이 이 스택 프레임과 연결 된 가장 작은 실제 주소를 반환 합니다.

`paddrMax`\
제한이 이 스택 프레임과 연결 된 가장 높은 실제 주소를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드에서 반환 하는 정보는 세션 디버그 관리자 (SDM)에서 스택 프레임을 정렬 하는 데 사용 됩니다.

 호출 스택이 증가 하는 것으로 가정 합니다. 즉, 새 스택 프레임은 점점 더 낮은 메모리 주소에 추가 됩니다. 런타임 아키텍처는이 가정에 맞는 물리적 스택 범위를 제공 해야 합니다.

## <a name="see-also"></a>추가 정보
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)

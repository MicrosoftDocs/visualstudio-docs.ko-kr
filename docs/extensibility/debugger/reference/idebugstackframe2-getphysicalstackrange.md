---
title: IDebugStackFrame2::GetPhysicalStackRange | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719662"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
스택 프레임과 연결된 물리적 주소 범위의 컴퓨터 종속 표현을 가져옵니다.

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
【아웃】 이 스택 프레임과 연결된 가장 낮은 물리적 주소를 반환합니다.

`paddrMax`\
【아웃】 이 스택 프레임과 연결된 가장 높은 물리적 주소를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드에서 반환되는 정보는 세션 디버그 관리자(SDM)에서 스택 프레임을 정렬하는 데 사용됩니다.

 호출 스택이 아래로 증가하는 것으로 가정합니다. 런타임 아키텍처는 이 가정과 일치하는 물리적 스택 범위를 제공해야 합니다.

## <a name="see-also"></a>참조
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)

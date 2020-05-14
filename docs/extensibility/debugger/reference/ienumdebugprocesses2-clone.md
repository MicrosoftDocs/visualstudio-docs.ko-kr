---
title: IEnumDebug프로세스2::클론 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2::Clone
helpviewer_keywords:
- IEnumDebugProcesses2::Clone
ms.assetid: 3d4196d3-5a80-4f76-b8b2-f72e80c8d406
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 931827891857d9a9f1364cd063b5fa30644257d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715909"
---
# <a name="ienumdebugprocesses2clone"></a>IEnumDebugProcesses2::Clone
현재 열거형의 복사본을 별도의 개체로 반환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Clone(
   IEnumDebugProcesses2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugProcesses2 ppEnum
);
```

## <a name="parameters"></a>매개 변수
`ppEnum`\
【아웃】 이 열거형의 복사본을 별도의 개체로 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 열거형의 복사본은 이 메서드가 호출될 때원본과 동일한 상태를 가짐입니다. 그러나 복사본과 원본의 상태는 분리되어 개별적으로 변경할 수 있습니다.

## <a name="see-also"></a>참조
- [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)

---
title: IDebug문서배치오프셋2::겟레인지 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd305b6506471a40de90fbd954e54461d2a139d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731633"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
현재 문서 위치의 범위를 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetRange(
   DWORD* pdwBegOffset,
   DWORD* pdwEndOffset
);
```

```csharp
public int GetRange(
   ref uint pdwBegOffset,
   ref uint pdwEndOffset
);
```

## <a name="parameters"></a>매개 변수
`pdwBegOffset`\
【인, 아웃】 범위의 시작 위치에 대한 간격띄우기입니다. 이 정보가 필요하지 않은 경우 이 매개 변수를 null 값으로 설정합니다.

`pdwEndOffset`\
【인, 아웃】 범위의 끝 위치에 대한 간격띄우기입니다. 이 정보가 필요하지 않은 경우 이 매개 변수를 null 값으로 설정합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 위치 중단점에 대한 문서 위치에 지정된 범위는 DE(디버그 엔진)에서 실제로 코드를 제공하는 문을 미리 검색하는 데 사용됩니다. 예를 들어, 다음 코드를 고려하세요.

```
Line 5: // comment
Line 6: x = 1;
```

 5호선은 디버깅 중인 프로그램에 코드를 제공하지 않습니다. 5줄에 중단점을 설정하는 디버거가 DE가 코드를 제공하는 첫 번째 줄에 대해 일정 금액을 검색하도록 하려는 경우 디버거는 중단점을 올바르게 배치할 수 있는 추가 후보 줄이 포함된 범위를 지정합니다. 그런 다음 DE는 중단점을 허용할 수 있는 줄을 찾을 때까지 해당 줄을 통해 앞으로 검색합니다.

## <a name="see-also"></a>참조
- [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)

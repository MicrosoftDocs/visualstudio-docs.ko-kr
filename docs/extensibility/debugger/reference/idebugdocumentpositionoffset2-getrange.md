---
title: 'IDebugDocumentPositionOffset2:: GetRange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ecb1e4aace5fb0c4f8c76b53a597b5b4b62110f5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879035"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
현재 문서 위치에 대 한 범위를 검색 합니다.

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
[in, out] 범위의 시작 위치에 대 한 오프셋입니다. 이 정보가 필요 하지 않은 경우이 매개 변수를 null 값으로 설정 합니다.

`pdwEndOffset`\
[in, out] 범위의 끝 위치에 대 한 오프셋입니다. 이 정보가 필요 하지 않은 경우이 매개 변수를 null 값으로 설정 합니다.

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 위치 중단점의 문서 위치에 지정 된 범위는 디버그 엔진 (DE)에서 실제로 코드를 적용 하는 문에 대해 미리 검색 하는 데 사용 됩니다. 예를 들어, 다음 코드를 고려하세요.

```
Line 5: // comment
Line 6: x = 1;
```

 5 번째 줄은 디버그 중인 프로그램에 코드를 적용 하지 않습니다. 줄 5에서 중단점을 설정 하는 디버거가 코드를 적용 하는 첫 번째 줄의 특정 크기를 검색 하도록 하려는 경우 디버거는 중단점을 올바르게 배치할 수 있는 추가 후보 줄을 포함 하는 범위를 지정 합니다. 그러면 DE는 중단점을 수락할 수 있는 줄을 찾을 때까지 해당 줄을 통해 앞으로 검색 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)

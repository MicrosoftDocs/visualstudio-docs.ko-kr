---
description: 이 문서 위치에 대 한 범위를 가져옵니다.
title: 'IDebugDocumentPosition2:: GetRange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5e886891c0d971bdad0916d5b243993e46a7ba57
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162721"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
이 문서 위치에 대 한 범위를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetRange( 
   TEXT_POSITION[] pBegPosition,
   TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>매개 변수
`pBegPosition`\
[in, out] 시작 위치로 채워진 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 구조체입니다. 이 정보가 필요 하지 않은 경우이 인수를 null 값으로 설정 합니다.

`pEndPosition`\
[in, out] 끝 위치로 채워진 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 구조체입니다. 이 정보가 필요 하지 않은 경우이 인수를 null 값으로 설정 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 위치 중단점의 문서 위치에 지정 된 범위는 디버그 엔진 (DE)에서 실제로 코드를 적용 하는 문에 대해 미리 검색 하는 데 사용 됩니다. 예를 들어, 다음 코드를 고려하세요.

```
Line 5: // comment
Line 6: x = 1;
```

 5 번째 줄은 디버그 중인 프로그램에 코드를 적용 하지 않습니다. 줄 5에서 중단점을 설정 하는 디버거가 코드를 적용 하는 첫 번째 줄의 특정 크기를 검색 하도록 하려는 경우 디버거는 중단점을 적절히 배치할 수 있는 추가 후보 줄을 포함 하는 범위를 지정 합니다. 그러면 DE는 중단점을 수락할 수 있는 줄을 찾을 때까지 해당 줄을 통해 앞으로 검색 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)

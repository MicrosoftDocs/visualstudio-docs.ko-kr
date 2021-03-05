---
description: 이 디버깅 엔진에서 디버그 하는 모든 모듈에 대해 필요한 경우 기호를 로드 합니다.
title: 'IDebugEngine3:: LoadSymbols | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4b4f210ef07ad10b35251582dd8a3c0fe3b0685
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153809"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
이 디버깅 엔진에서 디버그 하는 모든 모듈에 대해 필요한 경우 기호를 로드 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT LoadSymbols();
```

```csharp
int LoadSymbols();
```

## <a name="parameters"></a>매개 변수
 없음

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 디버깅 엔진에서 참조 하는 모든 모듈에 대 한 디버깅 기호를 로드 합니다. 기호는 아직 로드 되지 않은 경우에만 로드 됩니다. [Setsymbol 경로](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)에 대 한 호출로 설정 된 경로에서 기호가 검색 됩니다.

## <a name="see-also"></a>참고 항목
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)

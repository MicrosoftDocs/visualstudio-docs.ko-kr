---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7963d39601a0d3a90ca2daa7632902d7aa506de8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730803"
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

## <a name="see-also"></a>추가 정보
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)

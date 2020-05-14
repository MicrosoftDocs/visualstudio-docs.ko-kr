---
title: 아이데버그엔진3::세심볼패스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fbe5128900fa10147c747cbcba4129e96d4c4ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730667"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
디버깅 기호를 검색하는 경로 또는 경로를 설정합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetSymbolPath (
   LPOLESTR            szSymbolSearchPath,
   LPOLESTR            szSymbolCachePath,
   LOAD_SYMBOLS_FLAGS  Flags
);
```

```csharp
int SetSymbolPath(
   string                    szSymbolSearchPath,
   string                    szSymbolCachePath,
   enum_LOAD_SYMBOLS_FLAGS   Flags
);
```

## <a name="parameters"></a>매개 변수

`szSymbolSearchPath`\
【인】 기호 검색 경로 또는 경로를 포함하는 문자열입니다. 자세한 내용은 "비고"를 참조하십시오. null일 수 없습니다.

`szSymbolCachePath`\
【인】 기호를 캐시할 수 있는 로컬 경로를 포함하는 문자열입니다. null일 수 없습니다.

`Flags`\
【인】 사용되지 않음; 항상 0으로 설정합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 문자열은 `szSymbolSearchPath` 기호를 검색하기 위해 세미콜론으로 구분된 하나 이상의 경로 목록입니다. 이러한 경로는 로컬 경로, UNC 스타일 경로 또는 URL일 수 있습니다. 이러한 경로는 서로 다른 유형의 혼합일 수도 있습니다. 경로가 UNC(예: \\\Symserver\Symbols)인 경우 디버그 엔진은 경로가 기호 서버에 있는지 확인하고 해당 서버에서 기호를 로드하여 에 의해 `szSymbolCachePath`지정된 경로에서 이를 캐싱할 수 있어야 합니다.

 기호 경로에는 하나 이상의 캐시 위치가 포함될 수도 있습니다. 캐시는 우선 순위가 가장 높은 캐시를 먼저 우선 순위 순서로 나열하고 * 기호로 구분합니다. 다음은 그 예입니다.

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com
```

 [Load Symbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) 메서드는 기호의 실제 하중을 수행합니다.

## <a name="see-also"></a>참조
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)

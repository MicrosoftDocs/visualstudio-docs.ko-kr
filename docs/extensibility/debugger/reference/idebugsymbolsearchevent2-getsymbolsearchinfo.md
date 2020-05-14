---
title: 아이디버그 심볼서치검색이벤트2::GetSymbolSearch정보 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be498154a8141c61f114682893d0aaf8b841cf95
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718891"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
기호 로드 프로세스에 대한 결과를 검색하기 위해 이벤트 처리기에서 호출합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetSymbolSearchInfo(
   IDebugModule3**    pModule,
   BSTR*              pbstrDebugMessage,
   MODULE_INFO_FLAGS* pdwModuleInfoFlags
);
```

```csharp
int GetSymbolSearchInfo(
   IDebugModule3              pModule,
   ref string                 pbstrDebugMessage,
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags
);
```

## <a name="parameters"></a>매개 변수
`pModule`\
【아웃】 기호가 로드된 모듈을 나타내는 IDebugModule3 개체입니다.

`pbstrDebugMessage`\
【인, 아웃】 모듈의 오류 메시지가 포함된 문자열을 반환합니다. 오류가 없는 경우 이 문자열은 모듈의 이름만 포함하지만 비어 있지 않습니다.

> [!NOTE]
> [C++] `pbstrDebugMessage` 을 `NULL` 사용할 `SysFreeString`수 없으며 해제해야 합니다.

`pdwModuleInfoFlags`\
【아웃】 [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) 열거형의 플래그 조합으로 기호가 로드되었는지 여부를 나타냅니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 처리기가 모듈에 대한 디버깅 기호를 로드하려고 시도한 후 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) 이벤트를 수신하면 처리기가 이 메서드를 호출하여 해당 로드의 결과를 확인할 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)

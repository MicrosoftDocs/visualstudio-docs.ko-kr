---
title: 'IDebugCoreServer3:: EnableAutoAttach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7873480c979bba4f52203c02864d24aa88cf06cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907990"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
지정 된 디버그 엔진에 대해 자동 연결을 사용 하도록 설정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnableAutoAttach(
   GUID*     rgguidSpecificEngines,
   DWORD     celtSpecificEngines,
   LPCOLESTR pszStartPageUrl,
   BSTR*     pbstrSessionId
);
```

```csharp
int EnableAutoAttach(
   Guid[]     rgguidSpecificEngines,
   uint       celtSpecificEngines,
   string     pszStartPageUrl,
   out string pbstrSessionId
);
```

## <a name="parameters"></a>매개 변수
`rgguidSpecificEngines`\
진행 자동 연결로 표시할 각 디버그 엔진에 대 한 Guid의 배열입니다.

`celtSpecificEngines`\
진행 에 지정 된 엔진의 수입니다 `rgguidSpecificEngines` .

`pszStartPageUrl`\
진행 자동 연결 시 사용할 시작 URL입니다.

`pbstrSessionID`\
제한이 자동으로 연결 된 세션의 ID입니다.

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. 한 가지 오류 코드는 `E_AUTO_ATTACH_NOT_REGISTERED` 자동 연결 클래스 팩터리가 등록 되지 않았음을 나타내는입니다.

## <a name="remarks"></a>설명
 지정 된 URL과 연결 된 프로그램이 시작 되 면 지정 된 디버그 엔진이 자동으로 시작 되 고 연결 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)

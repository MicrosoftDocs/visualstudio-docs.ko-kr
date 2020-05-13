---
title: 아이디버그코어서버3:인에이블오토첨부 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d529bb80f79a3f2972e9349a2679bb528cc10463
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732914"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
지정된 디버그 엔진에 대해 자동으로 연결할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnableAutoAttach(
   GUID*     rgguidSpecificEngines,
   DWORD     celtSpecificEngines,
   LPCOLESTR pszStartPageUrl,
   BSTR*     pbstrSessionId
);
```

```csharp
int EnableAutoAttach(
   Guid[]     rgguidSpecificEngines,
   uint       celtSpecificEngines,
   string     pszStartPageUrl,
   out string pbstrSessionId
);
```

## <a name="parameters"></a>매개 변수
`rgguidSpecificEngines`\
【인】 각 디버그 엔진에 대한 GUID 배열을 사용하여 자동 연결로 표시합니다.

`celtSpecificEngines`\
【인】 에 지정된 엔진 `rgguidSpecificEngines`수입니다.

`pszStartPageUrl`\
【인】 자동 연결 할 때 사용할 시작 URL입니다.

`pbstrSessionID`\
【아웃】 자동 연결된 세션의 ID입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 한 가지 `E_AUTO_ATTACH_NOT_REGISTERED`오류 코드는 자동 연결 클래스 팩터리가 등록되지 되었음을 나타냅니다.

## <a name="remarks"></a>설명
 지정된 URL과 연결된 프로그램이 시작되면 지정된 디버그 엔진이 자동으로 시작되고 첨부됩니다.

## <a name="see-also"></a>참조
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)

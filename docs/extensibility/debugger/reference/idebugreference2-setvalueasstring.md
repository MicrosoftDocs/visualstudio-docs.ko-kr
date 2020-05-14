---
title: IDebug참조2::SetValueAsString | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsString
helpviewer_keywords:
- IDebugReference2::SetValueAsString
ms.assetid: 9a508ced-fd54-44f5-bb42-ec15c80384d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c8414ce5f53acec2a30ff681ff0bab8ddc919310
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720288"
---
# <a name="idebugreference2setvalueasstring"></a>IDebugReference2::SetValueAsString
문자열에서 참조 값을 설정합니다. 다음에 사용하도록 예약됩니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   DWORD     dwRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   dwRadix,
   uint   dwTimeout
);
```

## <a name="parameters"></a>매개 변수
`pszValue`\
【인】 문자열로 하는 값입니다.

`dwRadix`\
【인】 숫자 정보를 서식 지정하는 데 사용할 radix입니다.

`dwTimeout`\
【인】 이 메서드에서 반환하기 전에 기다릴 수 있는 최대 시간(밀리초)입니다. 무기한 `INFINITE` 대기하는 데 사용합니다.

## <a name="return-value"></a>Return Value
 항상 `E_NOTIMPL`를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

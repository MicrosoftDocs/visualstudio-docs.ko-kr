---
title: 'IDebugReference2:: SetValueAsString | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsString
helpviewer_keywords:
- IDebugReference2::SetValueAsString
ms.assetid: 9a508ced-fd54-44f5-bb42-ec15c80384d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0a2e481df64aeb4d5193ed011dc9f5cc669799b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956553"
---
# <a name="idebugreference2setvalueasstring"></a>IDebugReference2::SetValueAsString
문자열에서 참조의 값을 설정 합니다. 다음에 사용하도록 예약됩니다.

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
진행 값 (문자열)입니다.

`dwRadix`\
진행 숫자 정보의 서식을 지정 하는 데 사용할 기 수입니다.

`dwTimeout`\
진행 이 메서드에서 반환 될 때까지 대기 하는 최대 시간 (밀리초)입니다. `INFINITE`무기한 대기 하려면를 사용 합니다.

## <a name="return-value"></a>Return Value
 항상 `E_NOTIMPL`를 반환합니다.

## <a name="see-also"></a>참고 항목
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

---
title: 'IDebugSettingsCallback2:: GetMetricGuid | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetMetricGuid
ms.assetid: 91092763-3362-4857-adf0-231bc1254206
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c9c71ed9ee8d8a8be4931b17127fb1c1ade13252
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875837"
---
# <a name="idebugsettingscallback2getmetricguid"></a>IDebugSettingsCallback2::GetMetricGuid
해당 이름이 지정 된 메트릭의 고유 식별자를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetMetricGuid(
   LPCWSTR pszType,
   REFGUID guidSection,
   LPCWSTR pszMetric,
   GUID*   pguidValue
);
```

```csharp
private int GetMetricGuid(
   string   pszType,
   ref Guid guidSection,
   string   pszMetric,
   out Guid pguidValue
);
```

## <a name="parameters"></a>매개 변수
`pszType`\
진행 메트릭의 유형입니다.

`guidSection`\
진행 섹션의 고유 식별자입니다.

`pszMetric`\
진행 메트릭의 이름입니다.

`pguidValue`\
제한이 메트릭의 고유 식별자를 반환 합니다.

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)

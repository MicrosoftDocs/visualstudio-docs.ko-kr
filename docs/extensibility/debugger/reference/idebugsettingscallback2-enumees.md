---
description: 언어 및 공급 업체 식별자를 제공 하는 사용 가능한 식 계산기를 열거 합니다.
title: 'IDebugSettingsCallback2:: EnumEEs | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::EnumEEs
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7606bd46587c7141bddea0c822f08459f2d262d9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075668"
---
# <a name="idebugsettingscallback2enumees"></a>IDebugSettingsCallback2::EnumEEs
언어 및 공급 업체 식별자를 제공 하는 사용 가능한 식 계산기를 열거 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumEEs(
   DWORD  celtBuffer,
   GUID*  rgguidLang,
   GUID*  rgguidVendor,
   DWORD* pceltEEs
);
```

```csharp
public int EnumEEs(
   uint       celtBuffer,
   ref Guid   rgguidLang,
   ref Guid   rgguidVendor,
   ref uint[] pceltEEs
);
```

## <a name="parameters"></a>매개 변수
`celtBuffer`\
진행 버퍼의 요소 수 `pceltEEs` 입니다.

`rgguidLang`\
[in, out] 프로그래밍 언어에 대 한 고유 식별자입니다.

`rgguidVendor`\
[in, out] 공급 업체의 고유 식별자입니다.

`pceltEEs`\
[in, out] 식 계산기의 배열입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참조
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)

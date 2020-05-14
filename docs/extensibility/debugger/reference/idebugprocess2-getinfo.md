---
title: IDebugProcess2::GetInfo | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetInfo
helpviewer_keywords:
- IDebugProcess2::GetInfo
ms.assetid: 46021dce-bb97-46c3-b0cc-e5b3b68acc35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4f437c1a15b136d08ea7e57987c346844044228c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724018"
---
# <a name="idebugprocess2getinfo"></a>IDebugProcess2::GetInfo
프로세스에 대한 설명을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetInfo(
   PROCESS_INFO_FIELDS  Fields,
   PROCESS_INFO*        pProcessInfo
);
```

```csharp
int GetInfo(
   enum_PROCESS_INFO_FIELDS  Fields,
   PROCESS_INFO[]            pProcessInfo
);
```

## <a name="parameters"></a>매개 변수
`Fields`\
【인】 매개 변수의 필드를 채울 지 지정하는 PROCESS_INFO_FIELDS 열거형의 값 조합입니다. [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) `pProcessInfo`

`pProcessInfo`\
【아웃】 프로세스에 대한 설명으로 채워진 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) 구조입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)

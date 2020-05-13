---
title: 아이데버그엔진2::셋메트릭 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: caada8db1791d94e7a9632394cd4659bf8cec3a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730904"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
이 메서드는 메트릭으로 알려진 레지스트리 값을 설정합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
);
```

```csharp
int SetMetric(
   string pszMetric,
   object varValue
);
```

## <a name="parameters"></a>매개 변수
`pszMetric`\
【인】 메트릭 이름입니다.

`varValue`\
【인】 메트릭 값을 지정합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 메트릭은 디버그 엔진의 동작을 변경하거나 지원되는 기능을 보급하는 데 사용되는 레지스트리 값입니다. 이 메서드는 디버깅 함수에 대 한 [SDK 도우미의](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric`적절 한 형태로 호출을 전달할 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [디버깅을 위한 SDK 도우미](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

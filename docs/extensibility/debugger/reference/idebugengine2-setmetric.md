---
title: 'IDebugEngine2:: SetMetric | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4bb3c01b28f2d2c6e90616d389d9858d3346db72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933520"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
이 메서드는 메트릭 이라고 하는 레지스트리 값을 설정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
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
진행 메트릭 이름입니다.

`varValue`\
진행 메트릭 값을 지정 합니다.

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 메트릭은 디버그 엔진의 동작을 변경 하거나 지원 되는 기능을 알리는 데 사용 되는 레지스트리 값입니다. 이 메서드는 디버깅 함수에 대해 적절 한 형식의 [SDK 도우미에 대 한](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 호출을 전달할 수 있습니다 `SetMetric` .

## <a name="see-also"></a>참고 항목
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [디버깅을 위한 SDK 도우미](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

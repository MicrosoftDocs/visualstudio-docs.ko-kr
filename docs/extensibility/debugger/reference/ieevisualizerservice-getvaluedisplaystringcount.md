---
title: IEE비주얼라이저 서비스::겟밸류디스플레이스트링카운트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5c1a664594e55b8db21562a650c2c750668c2584
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717994"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
지정된 속성 또는 필드에 대해 표시할 값 문자열 수를 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetValueDisplayStringCount (
   DWORD         displayKind,
   IDebugField * propertyOrField,
   ULONG *       pcelt
);
```

```csharp
int GetValueDisplayStringCount (
   uint        displayKind,
   IDebugField propertyOrField,
   out ulong   pcelt
);
```

## <a name="parameters"></a>매개 변수
`displayKind`\
【인】 [디스플레이에서 값Kind](../../../extensibility/debugger/reference/displaykind.md) 열거.

`propertyOrField`\
【인】 속성 또는 필드를 나타내는 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스입니다.

`pcelt`\
【아웃】 표시할 값 문자열 수를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)

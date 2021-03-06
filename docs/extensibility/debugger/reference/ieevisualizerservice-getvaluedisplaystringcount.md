---
description: 지정 된 속성 또는 필드에 대해 표시할 값 문자열의 수를 검색 합니다.
title: 'IEEVisualizerService:: GetValueDisplayStringCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b77e2537e7581bb15f6458b4515d407fcfa1f827
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222850"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
지정 된 속성 또는 필드에 대해 표시할 값 문자열의 수를 검색 합니다.

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
진행 [Displaykind](../../../extensibility/debugger/reference/displaykind.md) 열거형의 값입니다.

`propertyOrField`\
진행 속성 또는 필드를 나타내는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스입니다.

`pcelt`\
제한이 표시할 값 문자열의 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참고 항목
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)

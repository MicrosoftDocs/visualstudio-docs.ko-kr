---
description: 이 메서드는 시각화 도우미 서비스를 만듭니다.
title: 'IEEVisualizerServiceProvider:: CreateVisualizerService | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b304dd8fe2845cf6c1201e6e128f8b89ec47b1b6
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222824"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
이 메서드는 시각화 도우미 서비스를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CreateVisualizerService(
   IDebugBinder*              binder,
   IDebugSymbolProvider*      pSymProv,
   IDebugAddress*             pAddress,
   IEEVisualizerDataProvider* dataProvider,
   IEEVisualizerService**     ppService
);
```

```csharp
int CreateVisualizerService(
   IDebugBinder binder,
   IDebugSymbolProvider      pSymProv,
   IDebugAddress             pAddress,
   IEEVisualizerDataProvider dataProvider,
   out IEEVisualizerService  ppService
);
```

## <a name="parameters"></a>매개 변수
`binder`\
진행 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)에 전달 된 [idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md) 개체입니다.

`pSymProv`\
진행 에 전달 된 [Idebug 공급자](../../../extensibility/debugger/reference/idebugsymbolprovider.md) 개체 `IDebugParsedExpression::EvaluateSync` 입니다.

`pAddress`\
진행 에 전달 된 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 개체 `IDebugParsedExression::EvaluateSync` 입니다.

`dataProvider`\
진행 식 계산기에서 제공 하는 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) 인터페이스를 구현 하는 개체입니다.

`ppService`\
제한이 만든 서비스입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 `binder`, `pSymProv` 및 `pAddress` 매개 변수가 모두 메서드에 전달 되었습니다 `IDebugParsedExpression::EvaluateSync` . `CreateVisualizerService` 는 `IDebugParsedExpression::EvaluateSync` 형식 시각화 도우미에 대 한 식 계산기의 지원의 일부로 서만 호출 됩니다.

## <a name="see-also"></a>참고 항목
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

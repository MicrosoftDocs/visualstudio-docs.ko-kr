---
title: IEE비주얼라이저데이터제공자 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a10f306b6c507f6db7add17931b8a38d926a37d9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718059"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 평가기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 평가기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 이 인터페이스는 형식 시각화 도우미를 통해 개체의 값을 변경할 수 있는 기능을 제공합니다.

## <a name="syntax"></a>구문

```
IEEVisualizerDataProvider : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 식 계산기는 형식 시각화 도우미를 통해 속성 개체에 대 한 데이터 수정을 지원 하기 위해이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스는 [Create VisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)에 대한 호출을 통해 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) 개체를 만드는 데 사용됩니다. 자세한 내용은 [데이터 시각화 및 보기를](../../../extensibility/debugger/visualizing-and-viewing-data.md) 참조하십시오.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드

|방법|설명|
|------------|-----------------|
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|이 시각화 도우미가 나타내는 개체(및 이후에 해당 값)를 업데이트할 수 있는지 여부를 결정합니다.|
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|이 시각화 도우미에 대 한 개체의 다시 평가 합니다.|
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|이 시각화 도우미에 대 한 기존 개체를 가져옵니다 (평가 수행 되지 않습니다).|
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|이 시각화 도우미에 대 한 개체를 업데이트 하 고 시각화 도우미가 제공 하는 값을 변경 합니다.|

## <a name="remarks"></a>설명
 시각화 도우미 서비스(IEEVisualizerService 인터페이스로 표시되고 [CreateVisualizerService에서](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)반환됨)는 인터페이스를 `IEEVisualizerDataProvider` 구현하는 개체에 대한 참조를 유지합니다. [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) 따라서 개체에 `IEEVisualizerDataProvider` 대한 참조를 `IEEVisualizerService` 유지 관리하는 경우 [IDebugProperty2를](../../../extensibility/debugger/reference/idebugproperty2.md) 구현하는 동일한 개체에 인터페이스를 구현해서는 안 됩니다. 권장되는 방법은 `IEEVisualizerDataProvider` `IDebugProperty2` 개체가 호출하지 `IUnknown::AddRef` 않고 대리하는 별도의 개체에 구현하는 것입니다.

## <a name="requirements"></a>요구 사항
 헤더: ee.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [데이터 시각화 및 보기](../../../extensibility/debugger/visualizing-and-viewing-data.md)

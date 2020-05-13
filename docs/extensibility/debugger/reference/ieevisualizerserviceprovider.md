---
title: IEE 비주얼라이저서비스제공자 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44d8a73589a4248736ac6c4d73814166056a1f90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717891"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 평가기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 평가기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 이 인터페이스는 IDE에 대한 형식 시각화 도우미 작업을 처리하는 데 사용되는 시각화 도우미 서비스를 만들 수 있는 메서드에 대한 액세스를 제공합니다.

## <a name="syntax"></a>구문

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 Visual Studio는 이 인터페이스를 구현하여 시각화 도우미 서비스 개체를 만들며,`CLSID`이 개체는 Visual Studio IDE에 형식 시각화 도우미의 클래스 아이디(들)를 제공하는 데 사용됩니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 식 계산기(EE)는 [GetEEService를](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) 호출하여 이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드

|방법|설명|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|시각화 도우미 서비스 생성|

## <a name="remarks"></a>설명
 인터페이스는 `IEEVisualizerServiceProvider` [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)를 구현하는 동안 가져옵니다. 이 인터페이스가 만드는 시각화 도우미 서비스는 EE가 구현하는 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스에 기능을 제공하는 데 사용됩니다. 또한 EE는 형식 시각화 도우미가 속성의 값을 보고 수정할 수 있는 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) 인터페이스를 구현합니다.

 이러한 [인터페이스가](../../../extensibility/debugger/visualizing-and-viewing-data.md) 상호 작용하는 방식에 대한 자세한 내용은 데이터 시각화 및 보기를 참조하십시오.

## <a name="requirements"></a>요구 사항
 헤더: ee.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [데이터 시각화 및 보기](../../../extensibility/debugger/visualizing-and-viewing-data.md)

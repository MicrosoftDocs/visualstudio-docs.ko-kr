---
title: IEEVisualizerDataProvider | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718059"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.

 이 인터페이스는 형식 시각화 도우미를 통해 개체의 값을 변경 하는 기능을 제공 합니다.

## <a name="syntax"></a>Syntax

```
IEEVisualizerDataProvider : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 식 계산기는 형식 시각화 도우미를 통해 속성 개체의 데이터 수정을 지원 하기 위해이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 이 인터페이스는 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)를 호출 하 여 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) 개체를 만드는 데 사용 됩니다. 자세한 내용은 [데이터 시각화 및 보기](../../../extensibility/debugger/visualizing-and-viewing-data.md) 를 참조 하세요.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드

|메서드|설명|
|------------|-----------------|
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|이 시각화 도우미가 나타내는 개체 (및 그 다음의 값)를 업데이트할 수 있는지 여부를 확인 합니다.|
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|이 시각화 도우미에 대 한 개체의 재평가를 강제로 수행 합니다.|
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|이 시각화 도우미에 대 한 기존 개체를 가져옵니다 (평가가 수행 되지 않음).|
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|이 시각화 도우미에 대 한 개체를 업데이트 하 여 시각화 도우미가 제공 하는 값을 변경 합니다.|

## <a name="remarks"></a>설명
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) 인터페이스로 표시 되 고 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)에서 반환 된 시각화 도우미 서비스는 인터페이스를 구현 하는 개체에 대 한 참조를 유지 합니다 `IEEVisualizerDataProvider` . 결과적으로 `IEEVisualizerDataProvider` 해당 개체가 개체에 대 한 참조를 유지 관리 하는 경우 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 을 구현 하는 동일한 개체에 대해 인터페이스를 구현 하면 안 됩니다. `IEEVisualizerService` 순환 참조 결과와 개체가 제거 될 때 교착 상태가 발생 합니다. 권장 되는 방법은를 `IEEVisualizerDataProvider` `IDebugProperty2` 호출 하지 않고 개체가 위임 하는 개별 개체에 대해를 구현 하는 것입니다 `IUnknown::AddRef` .

## <a name="requirements"></a>요구 사항
 헤더: ee. h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [데이터 시각화 및 보기](../../../extensibility/debugger/visualizing-and-viewing-data.md)

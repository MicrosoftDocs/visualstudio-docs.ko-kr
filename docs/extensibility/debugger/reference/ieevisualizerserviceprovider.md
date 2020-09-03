---
title: IEEVisualizerServiceProvider | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80717891"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.

 이 인터페이스는 IDE의 형식 시각화 도우미 작업을 처리 하는 데 사용 되는 시각화 도우미 서비스를 만들 수 있는 메서드에 대 한 액세스를 제공 합니다.

## <a name="syntax"></a>Syntax

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 Visual Studio는 시각화 도우미 서비스 개체를 만들기 위해이 인터페이스를 구현 하며,이 개체는 시각화 도우미의 클래스 Id를 `CLSID` Visual STUDIO IDE에 제공 하는 데 사용 됩니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 식 계산기 (EE)는 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) 을 호출 하 여이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드

|메서드|설명|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|시각화 도우미 서비스를 만듭니다.|

## <a name="remarks"></a>설명
 `IEEVisualizerServiceProvider` [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)을 구현 하는 동안 인터페이스를 가져옵니다. 이 인터페이스에서 생성 하는 시각화 도우미 서비스는 EE가 구현을 담당 하는 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스에 기능을 제공 하는 데 사용 됩니다. 또한 EE는 형식 시각화 도우미가 속성의 값을 보고 수정할 수 있도록 하는 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) 인터페이스를 구현 합니다.

 이러한 인터페이스가 상호 작용 하는 방법에 대 한 자세한 내용은 [데이터 시각화 및 보기](../../../extensibility/debugger/visualizing-and-viewing-data.md) 를 참조 하세요.

## <a name="requirements"></a>요구 사항
 헤더: ee. h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [데이터 시각화 및 보기](../../../extensibility/debugger/visualizing-and-viewing-data.md)

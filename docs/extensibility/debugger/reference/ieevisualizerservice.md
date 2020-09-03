---
title: IEEVisualizerService | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40d21dcc9b1da0e1e2250adcfad59b3ef46a2113
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80717935"
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.

 이 인터페이스는 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 및 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 인터페이스에 기능을 제공 하는 키 메서드를 구현 합니다.

## <a name="syntax"></a>Syntax

```
IEEVisualizerService : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 Visual Studio에서는 식 계산기 (EE)가 형식 시각화 도우미를 지원할 수 있도록이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 EE는 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) 를 호출 하 여 형식 시각화 도우미에 대 한 지원의 일부로이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드

|메서드|설명|
|------------|-----------------|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|이 서비스에서 알고 있는 사용자 지정 뷰어 수를 검색 합니다.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|사용자 지정 뷰어 목록을 검색 합니다.|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|속성에 대 한 프록시 개체를 반환 합니다.|
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|지정 된 속성 또는 필드에 대해 표시할 값 문자열의 수를 검색 합니다.|

## <a name="remarks"></a>설명
 IDE는 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스를 사용 하 여 속성에 대 한 사용자 지정 뷰어 또는 형식 시각화 도우미가 있는지 확인 합니다. EE는 시각화 도우미 서비스 ( [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)사용)를 만들어 `IDebugProperty3` 및 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) (속성의 값 보기 및 변경 지원) 인터페이스를 지원 하 고 형식 시각화 도우미를 지원할 수 있습니다.

 EE에서 자체를 구현 하는 사용자 지정 뷰어를 포함 하는 경우 EE는 `CLSID` 이러한 사용자 지정 뷰어의를 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)에서 반환 된 목록의 끝에 추가할 수 있습니다. 이를 통해 EE는 형식 시각화 도우미와 자체 사용자 지정 뷰어를 모두 지원할 수 있습니다. [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) 가 사용자 지정 뷰어를 추가 하는 것을 반영 해야 합니다.

 시각화 도우미와 뷰어 간의 차이점에 대 한 설명은 [형식 시각화 도우미 및 사용자 지정 뷰어](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) 를 참조 하세요.

## <a name="requirements"></a>요구 사항
 헤더: ee. h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)
- [형식 시각화 도우미 및 사용자 지정 뷰어](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

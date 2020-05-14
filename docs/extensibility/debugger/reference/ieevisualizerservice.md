---
title: IEE비주얼라이저서비스 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717935"
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 평가기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 평가기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 이 인터페이스는 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 및 [IPropertyProxyESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 인터페이스에 기능을 제공하는 주요 메서드를 구현합니다.

## <a name="syntax"></a>구문

```
IEEVisualizerService : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 Visual Studio는 식 계산기(EE)가 형식 시각화 도우미를 지원할 수 있도록 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 EE는 [CreateVisualizerService를](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) 호출하여 형식 시각화 도우미에 대한 지원의 일부로 이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드

|방법|설명|
|------------|-----------------|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|이 서비스가 알고 있는 사용자 지정 뷰어 수를 검색합니다.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|사용자 지정 뷰어 목록을 검색합니다.|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|속성에 대한 프록시 개체를 반환합니다.|
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|지정된 속성 또는 필드에 대해 표시할 값 문자열 수를 검색합니다.|

## <a name="remarks"></a>설명
 IDE는 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스를 사용하여 속성에 대한 사용자 지정 뷰어 또는 형식 시각화 도우미가 있는지 확인합니다. 시각화 도우미 서비스(CreateVisualizerService 사용)를 만들면 EE는 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) `IDebugProperty3` 및 [IPropertyProxyESide(속성값](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 보기 및 변경 지원) 인터페이스에 기능을 제공하여 형식 시각화 도우미를 지원할 수 있습니다.

 EE에 구현하는 사용자 지정 뷰어가 있는 경우 `CLSID`EE는 [GetCustomViewerList에서](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)반환한 목록의 끝에 해당 사용자 지정 뷰어의 s를 추가할 수 있습니다. 이를 통해 EE는 형식 시각화 도우미와 자체 사용자 지정 뷰어를 모두 지원할 수 있습니다. [GetCustomViewerCount은](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) 사용자 지정 뷰어의 추가를 반영해야 합니다.

 시각화 도우미와 뷰어간의 차이점에 대한 설명은 [유형 시각화 도우미 및 맞춤 뷰어를](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) 참조하세요.

## <a name="requirements"></a>요구 사항
 헤더: ee.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)
- [형식 시각화 도우미 및 사용자 지정 뷰어](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

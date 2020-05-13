---
title: 유형 시각화 도우미 및 사용자 지정 뷰어 구현 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2ebbb5c8e27df4ae4baf2d9a9f1c3314188e2b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738500"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>유형 시각화 도우미 및 사용자 지정 뷰어 구현
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 계산기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 유형 시각화 도우미 및 사용자 지정 뷰어를 사용하면 사용자가 간단한 육각형 숫자 덤프보다 더 의미 있는 방식으로 특정 형식의 데이터를 볼 수 있습니다. 식 평가기(EE)는 사용자 지정 뷰어를 특정 유형의 데이터 또는 변수와 연결할 수 있습니다. 이러한 사용자 지정 뷰어는 EE에 의해 구현됩니다. 또한 EE는 다른 타사 공급업체 또는 최종 사용자로부터 올 수 있는 외부 형식 시각화 도우미를 지원할 수도 있습니다.

## <a name="discussion"></a>토론

### <a name="type-visualizers"></a>유형 시각화 도우미
 Visual Studio는 모든 개체가 시계 창에 표시될 형식 시각화 도우미 및 사용자 지정 뷰어 목록을 요청합니다. 식 계산기(EE)는 형식 시각화 도우미 및 사용자 지정 뷰어를 지원하려는 모든 유형에 대해 이러한 목록을 제공합니다. [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) 및 [GetCustomViewerList에](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 대한 호출은 형식 시각화 도우미 및 사용자 지정 뷰어에 액세스하는 전체 프로세스를 시작합니다(호출 시퀀스에 대한 자세한 내용은 [데이터 시각화 및 보기](../../extensibility/debugger/visualizing-and-viewing-data.md) 참조).

### <a name="custom-viewers"></a>맞춤 시청자
 사용자 지정 뷰어는 특정 데이터 형식에 대해 EE에서 구현되며 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) 인터페이스로 표시됩니다. 사용자 지정 뷰어는 특정 사용자 지정 뷰어를 구현하는 EE가 실행 중일 때만 사용할 수 있으므로 형식 시각화 도우미만큼 유연하지 않습니다. 사용자 지정 뷰어를 구현하는 것은 형식 시각화 도우미에 대한 지원을 구현하는 것보다 간단합니다. 그러나 형식 시각화 도우미를 지원하면 최종 사용자가 데이터를 시각화할 수 있는 유연성을 극대화할 수 있습니다. 이 설명의 나머지 부분에서는 유형 시각화 도우미만 다릅니다.

## <a name="interfaces"></a>인터페이스
 EE는 Visual Studio에서 사용할 형식 시각화 도우미를 지원하기 위해 다음 인터페이스를 구현합니다.

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  EE는 형식 시각화 도우미를 지원하기 위해 다음 인터페이스를 사용합니다.

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>참조
- [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [데이터 시각화 및 보기](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)

---
title: 데이터 시각화 및 보기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b5f984e6c6a3c1c8f3835dfa93a8679ae16680a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712373"
---
# <a name="visualizing-and-viewing-data"></a>데이터 시각화 및 보기
유형 시각화 도우미와 사용자 지정 뷰어는 개발자에게 빠르게 의미 있는 방식으로 데이터를 표시합니다. 식 평가기(EE)는 타사 유형 시각화 도우미를 지원할 수 있으며 사용자 지정 뷰어를 제공할 수 있습니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]는 [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) 메서드를 호출하여 개체의 형식과 연관된 형식 시각화 도우미 및 사용자 지정 뷰어 수를 결정합니다. 하나 이상의 형식 시각화 도우미 또는 사용자 지정 뷰어를 사용할 수 있는 경우 Visual Studio는 [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 메서드를 호출하여 해당 시각화 도우미 및 뷰어 목록(실제로 시각화 도우미 및 뷰어를 구현하는 s 목록)을 검색하여 사용자에게 제공합니다.

## <a name="supporting-type-visualizers"></a>유형 시각화 도우미 지원
 EE가 형식 시각화 도우미를 지원하기 위해 구현해야 하는 인터페이스는 여러 가지가 있습니다. 이러한 인터페이스는 속성 데이터에 액세스하는 형식 시각화 도우미와 인터페이스를 나열하는 인터페이스의 두 가지 범주로 나눌 수 있습니다.

### <a name="listing-type-visualizers"></a>목록 유형 시각화 도우미
 EE는 구현 `IDebugProperty3::GetCustomViewerCount` 및 `IDebugProperty3::GetCustomViewerList`에서 형식 시각화 도우미를 나열하는 것을 지원합니다. 이러한 메서드는 해당 [메서드GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) 및 [GetCustomViewerList에](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)대 한 호출을 전달 합니다.

 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) 는 [Create VisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)를 호출하여 가져옵니다. 이 메서드에는 [EvaluateSync에](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)전달된 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder3.md) 인터페이스에서 가져온 [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder.md) 인터페이스가 필요합니다. `IEEVisualizerServiceProvider::CreateVisualizerService`또한 에 전달된 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) 및 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) `IDebugParsedExpression::EvaluateSync`인터페이스가 필요합니다. `IEEVisualizerService` 인터페이스를 만드는 데 필요한 마지막 인터페이스는 [EEE가 구현하는 IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) 인터페이스입니다. 이 인터페이스를 사용하면 시각화되는 속성을 변경할 수 있습니다. 모든 속성 데이터는 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) 인터페이스에 캡슐화되며 EE에서도 구현됩니다.

### <a name="accessing-property-data"></a>속성 데이터에 액세스
 속성 데이터에 액세스하는 것은 [IPropertyProxyESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) 인터페이스를 통해 수행됩니다. 이 인터페이스를 얻으려면 Visual Studio호출 [QueryInterface](/cpp/atl/queryinterface) 속성 개체에 [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) 인터페이스 [(IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스를 구현 하는 동일한 개체에 구현) 다음 `IPropertyProxyEESide` 인터페이스를 얻기 위해 [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) 메서드를 호출 합니다.

 인터페이스안팎으로 `IPropertyProxyEESide` 전달되는 모든 데이터는 [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) 인터페이스에 캡슐화됩니다. 이 인터페이스는 바이트 배열을 나타내며 Visual Studio와 EE 모두에서 구현됩니다. 속성의 데이터를 변경하려는 경우 Visual Studio는 `IEEDataStorage` 새 데이터를 보유하는 개체를 만들고 해당 데이터 개체를 사용하여 `IEEDataStorage` [CreateReplacementObject를](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) 호출하여 속성의 데이터를 업데이트하기 위해 [InPlaceUpdateObject에](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) 전달되는 새 개체를 가져옵니다. `IPropertyProxyEESide::CreateReplacementObject`이를 통해 EE는 인터페이스를 구현하는 자체 클래스를 인스턴스화할 수 있습니다. `IEEDataStorage`

## <a name="supporting-custom-viewers"></a>맞춤 시청자 지원
 플래그는 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` [개체에](../../extensibility/debugger/reference/debug-property-info.md) `dwAttrib` 연결된 사용자 지정 뷰어가 있음을 나타내기 위해 DEBUG_PROPERTY_INFO 구조의 필드에 설정됩니다(GetPropertyInfo 호출에 의해 반환됨). [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 이 플래그를 설정하면 Visual Studio는 [쿼리 인터페이스를](/cpp/atl/queryinterface)사용하여 [IDebugProperty2 인터페이스에서 IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스를 가져옵니다. [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

 사용자가 사용자 지정 뷰어를 선택하면 Visual Studio는 메서드에서 제공하는 뷰어를 `CLSID` `IDebugProperty3::GetCustomViewerList` 사용하여 사용자 지정 뷰어를 인스턴스화합니다. 그런 다음 Visual Studio에서 [DisplayValue를](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) 호출하여 사용자에게 값을 표시합니다.

 일반적으로 `IDebugCustomViewer::DisplayValue` 데이터의 읽기 전용 보기를 제공합니다. 데이터를 변경할 수 있도록 EE는 속성 개체의 데이터 변경을 지원하는 사용자 지정 인터페이스를 구현해야 합니다. 메서드는 `IDebugCustomViewer::DisplayValue` 이 사용자 지정 인터페이스를 사용하여 데이터 변경을 지원합니다. 메서드는 인수로 전달 된 `IDebugProperty2` 인터페이스에서 사용자 `pDebugProperty` 지정 인터페이스를 찾습니다.

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>유형 시각화 도우미와 사용자 지정 뷰어 모두 지원
 EE는 [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) 및 [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 메서드에서 형식 시각화 도우미 및 사용자 지정 뷰어를 모두 지원할 수 있습니다. 먼저 EE는 [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) 메서드에서 반환하는 값에 제공하는 사용자 지정 뷰어 수를 추가합니다. 둘째, EE는 `CLSID` [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) 메서드에 의해 반환 된 목록에 자체 사용자 지정 뷰어의 s를 추가 합니다.

## <a name="see-also"></a>참조
- [작업 디버깅](../../extensibility/debugger/debugging-tasks.md)
- [시각화 도우미 및 사용자 지정 뷰어 유형](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

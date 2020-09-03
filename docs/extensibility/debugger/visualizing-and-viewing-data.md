---
title: 데이터 시각화 및 보기 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712373"
---
# <a name="visualizing-and-viewing-data"></a>데이터 시각화 및 보기
시각화 도우미 및 사용자 지정 뷰어는 개발자에 게 신속 하 게 의미 있는 방식으로 데이터를 제공 합니다. 식 계산기 (EE)는 타사 형식 시각화 도우미를 지원할 뿐만 아니라 고유한 사용자 지정 뷰어를 제공할 수 있습니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)][GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) 메서드를 호출 하 여 개체의 형식과 연결 된 형식 시각화 도우미 및 사용자 지정 뷰어 수를 결정 합니다. 하나 이상의 형식 시각화 도우미가 나 사용자 지정 뷰어를 사용할 수 있는 경우 Visual Studio는 [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 메서드를 호출 하 여 해당 시각화 도우미 및 뷰어 목록을 검색 하 고 (실제로는 시각화 도우미와 뷰어를 구현 하는 목록) 사용자에 게 표시 합니다.

## <a name="supporting-type-visualizers"></a>지원 형식 시각화 도우미
 EE에서 형식 시각화 도우미를 지원 하기 위해 구현 해야 하는 다양 한 인터페이스가 있습니다. 이러한 인터페이스는 형식 시각화 도우미와 속성 데이터에 액세스 하는 인터페이스를 나열 하는 인터페이스 라는 두 개의 광범위 한 범주로 나눌 수 있습니다.

### <a name="listing-type-visualizers"></a>형식 시각화 도우미 나열
 EE는 및의 구현에서 형식 시각화 도우미 목록을 지원 `IDebugProperty3::GetCustomViewerCount` 합니다 `IDebugProperty3::GetCustomViewerList` . 이러한 메서드는 해당 메서드 [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) 및 [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)에 대 한 호출을 전달 합니다.

 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) 는 [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)를 호출 하 여 가져옵니다. 이 메서드에는 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)에 전달 된 [idebugbinder](../../extensibility/debugger/reference/idebugbinder.md) 인터페이스에서 가져온 [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) 인터페이스가 필요 합니다. `IEEVisualizerServiceProvider::CreateVisualizerService` 에는에 전달 된 [Idebug기호 공급자](../../extensibility/debugger/reference/idebugsymbolprovider.md) 및 [idebugaddress](../../extensibility/debugger/reference/idebugaddress.md) 인터페이스도 필요 `IDebugParsedExpression::EvaluateSync` 합니다. 인터페이스를 만드는 데 필요한 최종 인터페이스는 `IEEVisualizerService` EE에서 구현 하는 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) 인터페이스입니다. 이 인터페이스를 사용 하면 시각화 중인 속성에 대 한 변경 내용을 적용할 수 있습니다. 모든 속성 데이터는 EE에 의해 구현 되는 [Idebugobject](../../extensibility/debugger/reference/idebugobject.md) 인터페이스에 캡슐화 되어 있습니다.

### <a name="accessing-property-data"></a>속성 데이터 액세스
 속성 데이터에 액세스 하는 작업은 [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) 인터페이스를 통해 수행 됩니다. 이 인터페이스를 얻기 위해 Visual Studio는 property 개체에 대해 [QueryInterface](/cpp/atl/queryinterface) 를 호출 하 여 [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스를 구현 하는 동일한 개체에 구현 된 [ipropertyproxyprovider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) 인터페이스를 가져온 다음, [getpropertyproxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) 메서드를 호출 하 여 인터페이스를 가져옵니다 `IPropertyProxyEESide` .

 인터페이스로 전달 및 전달 되는 모든 데이터 `IPropertyProxyEESide` 는 [Ieedatastorage](../../extensibility/debugger/reference/ieedatastorage.md) 인터페이스에 캡슐화 됩니다. 이 인터페이스는 바이트 배열을 나타내며 Visual Studio와 EE 모두에 의해 구현 됩니다. 속성의 데이터를 변경 하는 경우 Visual Studio는 `IEEDataStorage` 새 데이터를 보유 하는 개체를 만들고 해당 데이터 개체를 사용 하 여 [Creatrereementementobject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) 를 호출 하 여 `IEEDataStorage` 속성의 데이터를 업데이트 하는 새 개체를 [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) 에 전달 합니다. `IPropertyProxyEESide::CreateReplacementObject` EE에서 인터페이스를 구현 하는 자체 클래스를 인스턴스화할 수 있도록 허용 `IEEDataStorage` 합니다.

## <a name="supporting-custom-viewers"></a>사용자 지정 뷰어 지원
 플래그는 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` `dwAttrib` [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)에 대 한 호출에 의해 반환 되는 [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) 구조체의 필드에 설정 되며, 개체에 연결 된 사용자 지정 뷰어가 있음을 나타내는 데 사용 됩니다. 이 플래그가 설정 되 면 Visual Studio는 [QueryInterface](/cpp/atl/queryinterface)를 사용 하 여 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스에서 [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스를 가져옵니다.

 사용자가 사용자 지정 뷰어를 선택 하는 경우 Visual Studio는 메서드에서 제공 하는 뷰어를 사용 하 여 사용자 지정 뷰어를 인스턴스화합니다 `CLSID` `IDebugProperty3::GetCustomViewerList` . 그런 다음 Visual Studio에서 [Displayvalue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) 를 호출 하 여 사용자에 게 값을 표시 합니다.

 일반적으로는 `IDebugCustomViewer::DisplayValue` 데이터의 읽기 전용 뷰를 표시 합니다. 데이터를 변경할 수 있도록 EE는 속성 개체의 데이터 변경을 지 원하는 사용자 지정 인터페이스를 구현 해야 합니다. `IDebugCustomViewer::DisplayValue`메서드는이 사용자 지정 인터페이스를 사용 하 여 데이터 변경을 지원 합니다. 메서드는 인수로 전달 된 인터페이스에서 사용자 지정 인터페이스를 찾습니다 `IDebugProperty2` `pDebugProperty` .

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>형식 시각화 도우미 및 사용자 지정 뷰어 모두 지원
 EE는 [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) 및 [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 메서드에서 형식 시각화 도우미 및 사용자 지정 뷰어를 모두 지원할 수 있습니다. 먼저 EE는 [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) 메서드에서 반환 하는 값에 제공 되는 사용자 지정 뷰어 수를 추가 합니다. 두 번째로, EE는 `CLSID` 자체 사용자 지정 뷰어를 [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) 메서드에서 반환 된 목록에 추가 합니다.

## <a name="see-also"></a>추가 정보
- [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)
- [형식 시각화 도우미 및 사용자 지정 뷰어](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

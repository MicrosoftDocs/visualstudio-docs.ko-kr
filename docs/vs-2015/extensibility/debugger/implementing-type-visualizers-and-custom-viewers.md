---
title: 형식 시각화 도우미 및 사용자 지정 뷰어 구현 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b780f2115400fd43e8915a5109c960cab99bf131
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843329"
---
# <a name="implementing-type-visualizers-and-custom-viewers"></a>형식 시각화 도우미 및 사용자 지정 뷰어 구현
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.  
  
 형식 시각화 도우미 및 사용자 지정 뷰어를 사용 하면 사용자가 간단한 16 진수 덤프 보다 더 의미 있는 방식으로 특정 형식의 데이터를 볼 수 있습니다. 식 계산기 (EE)는 사용자 지정 뷰어를 특정 형식의 데이터 나 변수와 연결할 수 있습니다. 이러한 사용자 지정 뷰어는 EE에서 구현 합니다. EE는 다른 타사 공급 업체 또는 최종 사용자가 제공 하는 외부 형식 시각화 도우미도 지원할 수 있습니다.  
  
## <a name="discussion"></a>토론(Discussion)  
  
### <a name="type-visualizers"></a>형식 시각화 도우미  
 Visual Studio에서는 조사식 창에 표시 되는 모든 개체에 대 한 형식 시각화 도우미 및 사용자 지정 뷰어 목록을 요청 합니다. EE (식 계산기)는 형식 시각화 도우미 및 사용자 지정 뷰어를 지원 하려고 하는 모든 형식에 대해 이러한 목록을 제공 합니다. [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) 및 [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 에 대 한 호출은 형식 시각화 도우미 및 사용자 지정 뷰어에 액세스 하는 전체 프로세스를 시작 합니다. 호출 시퀀스에 대 한 자세한 내용은 [데이터 시각화 및 보기](../../extensibility/debugger/visualizing-and-viewing-data.md) 를 참조 하세요.  
  
### <a name="custom-viewers"></a>사용자 지정 뷰어  
 사용자 지정 뷰어는 특정 데이터 형식에 대해 EE에서 구현 되며 [Idebugcustomviewer](../../extensibility/debugger/reference/idebugcustomviewer.md) 인터페이스로 표시 됩니다. 사용자 지정 뷰어는 특정 사용자 지정 뷰어를 구현 하는 EE를 실행 하는 경우에만 사용할 수 있으므로 형식 시각화 도우미 만큼 유연 하지 않습니다. 사용자 지정 뷰어 구현은 형식 시각화 도우미에 대 한 지원을 구현 하는 것 보다 간단 합니다. 그러나 지원 형식 시각화 도우미는 최종 사용자가 자신의 데이터를 시각화할 수 있는 최대 유연성을 제공 합니다. 이 논의의 나머지 부분에서는 형식 시각화 도우미만 다룹니다.  
  
## <a name="interfaces"></a>인터페이스  
 EE는 다음과 같은 인터페이스를 구현 하 여 Visual Studio에서 사용 되는 형식 시각화 도우미를 지원 합니다.  
  
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
  EE는 다음과 같은 인터페이스를 사용 하 여 형식 시각화 도우미를 지원 합니다.  
  
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## <a name="see-also"></a>참고 항목  
 [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [데이터 시각화 및 보기](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)

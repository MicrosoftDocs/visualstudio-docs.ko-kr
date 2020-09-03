---
title: IDebugCustomViewer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f94fe0301777a615fa6dc567311c493ff55a90a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196292"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스를 사용 하면 식 계산기 (EE)에서 필요한 모든 형식으로 속성 값을 표시할 수 있습니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 EE는이 인터페이스를 구현 하 여 속성의 값을 사용자 지정 형식으로 표시 합니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 COM의 함수에 대 한 호출은 `CoCreateInstance` 이 인터페이스를 인스턴스화합니다. `CLSID`에 전달 된는 `CoCreateInstance` 레지스트리에서 가져옵니다. [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 에 대 한 호출은 레지스트리의 위치를 가져옵니다. 자세한 내용은 설명 및 예제를 참조 하세요.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 이 인터페이스는 다음 메서드를 구현 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|지정 된 값을 표시 하는 데 필요한 모든 항목을 수행 합니다.|  
  
## <a name="remarks"></a>설명  
 이 인터페이스는 데이터 테이블이 나 다른 복합 속성 형식 등의 일반적인 방법으로 속성 값을 표시할 수 없을 때 사용 됩니다. 인터페이스에 표시 되는 사용자 지정 뷰어는 `IDebugCustomViewer` EE와 관계 없이 특정 형식의 데이터를 표시 하는 외부 프로그램인 형식 시각화 도우미와 다릅니다. EE는 해당 EE와 관련 된 사용자 지정 뷰어를 구현 합니다. 사용자는 사용할 시각화 도우미 유형을 형식 시각화 도우미 나 사용자 지정 뷰어로 선택 합니다. 이 프로세스에 대 한 자세한 내용은 [데이터 시각화 및 보기](../../../extensibility/debugger/visualizing-and-viewing-data.md) 를 참조 하세요.  
  
 사용자 지정 뷰어는 EE와 동일한 방식으로 등록 되므로 언어 GUID와 공급 업체 GUID가 필요 합니다. 정확한 메트릭 (또는 레지스트리 항목 이름)은 EE에만 알려집니다. 이 메트릭은 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)에 대 한 호출에 의해 반환 되는 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) 구조에서 반환 됩니다. 메트릭에 저장 된 값은 `CLSID` COM의 함수에 전달 되는입니다 `CoCreateInstance` (예제 참조).  
  
 [디버깅을 위한 SDK 도우미](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 함수를 `SetEEMetric` 사용 하 여 사용자 지정 뷰어를 등록할 수 있습니다. `Debugging SDK Helpers`사용자 지정 뷰어가 필요한 특정 레지스트리 키에 대 한의 "식 계산기" 레지스트리 섹션을 참조 하세요. 사용자 지정 뷰어에는 EE의 구현자에 의해 정의 되는 메트릭 하나만 필요 하지만 식 계산기에는 미리 정의 된 여러 메트릭이 필요 합니다.  
  
 일반적으로 [Displayvalue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) 에 제공 된 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스에는 문자열을 제외 하 고 속성 값을 변경 하는 메서드가 없기 때문에 사용자 지정 뷰어는 데이터에 대 한 읽기 전용 뷰를 제공 합니다. 모든 데이터 블록 변경을 지원 하기 위해 EE는 인터페이스를 구현 하는 동일한 개체에서 사용자 지정 인터페이스를 구현 합니다 `IDebugProperty3` . 그런 다음이 사용자 지정 인터페이스는 임의의 데이터 블록을 변경 하는 데 필요한 메서드를 제공 합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>예  
 이 예제에서는 속성에서 사용자 지정 뷰어를 포함 하는 경우 속성에서 첫 번째 사용자 지정 뷰어를 가져오는 방법을 보여 줍니다.  
  
```cpp#  
IDebugCustomViewer *GetFirstCustomViewer(IDebugProperty2 *pProperty)  
{  
    // This string is typically defined globally.  For this example, it  
    // is defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugCustomViewer *pViewer = NULL;  
    if (pProperty != NULL) {  
        CComQIPtr<IDebugProperty3> pProperty3(pProperty);  
        if (pProperty3 != NULL) {  
            HRESULT hr;  
            ULONG viewerCount = 0;  
            hr = pProperty3->GetCustomViewerCount(&viewerCount);  
            if (viewerCount > 0) {  
                ULONG viewersFetched = 0;  
                DEBUG_CUSTOM_VIEWER viewerInfo = { 0 };  
                hr = pProperty3->GetCustomViewerList(0,  
                                                     1,  
                                                     &viewerInfo,  
                                                     &viewersFetched);  
                if (viewersFetched == 1) {  
                    CLSID clsidViewer = { 0 };  
                    CComPtr<IDebugCustomViewer> spCustomViewer;  
                    // Get the viewer's CLSID from the registry.  
                    ::GetEEMetric(viewerInfo.guidLang,  
                                  viewerInfo.guidVendor,  
                                  viewerInfo.bstrMetric,  
                                  &clsidViewer,  
                                  strRegistrationRoot);  
                    if (!IsEqualGUID(clsidViewer,GUID_NULL)) {  
                        // Instantiate the custom viewer.  
                        spCustomViewer.CoCreateInstance(clsidViewer);  
                        if (spCustomViewer != NULL) {  
                            pViewer = spCustomViewer.Detach();  
                        }  
                    }  
                }  
            }  
        }  
    }  
    return(pViewer);  
}  
```  
  
## <a name="see-also"></a>관련 항목  
 [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [디버깅을 위한 SDK 도우미](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)

---
title: 아이디버그커스텀뷰어 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c44d2289180ece35725b9258e9d20abeb3a4cac3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732423"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
이 인터페이스를 사용하면 식 계산기(EE)가 필요한 형식으로 속성값을 표시할 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
EE는 이 인터페이스를 구현하여 사용자 지정 형식으로 속성의 값을 표시합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
COM 함수에 `CoCreateInstance` 대한 호출은 이 인터페이스를 인스턴스화합니다. `CoCreateInstance` 전달된 것은 `CLSID` 레지스트리에서 가져옵니다. [GetCustomViewerList에](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 대한 호출은 레지스트리의 위치를 가져옵니다. 자세한 내용은 설명과 예제를 참조하십시오.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
이 인터페이스는 다음 방법을 구현합니다.

|방법|설명|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|지정된 값을 표시하는 데 필요한 모든 작업을 수행합니다.|

## <a name="remarks"></a>설명
이 인터페이스는 데이터 테이블이나 다른 복잡한 속성 유형과 같이 속성값을 정상적인 수단으로 표시할 수 없는 경우에 사용됩니다. `IDebugCustomViewer` 인터페이스로 표시되는 사용자 지정 뷰어는 EE에 관계없이 특정 형식의 데이터를 표시하기 위한 외부 프로그램인 형식 시각화 도우미와 다릅니다. EE는 해당 EE에 특정한 사용자 지정 뷰어를 구현합니다. 사용자는 사용할 시각화 도우미 유형(형식 시각화 도우미 또는 사용자 지정 뷰어)을 선택합니다. 이 프로세스에 대한 자세한 내용은 [데이터 시각화 및 보기를](../../../extensibility/debugger/visualizing-and-viewing-data.md) 참조하십시오.

사용자 지정 뷰어는 EE와 동일한 방식으로 등록되므로 언어 GUID와 공급업체 GUID가 필요합니다. 정확한 메트릭(또는 레지스트리 항목 이름)은 EE에만 알려져 있습니다. 이 메트릭은 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) 구조에서 반환되며 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)에 대한 호출을 통해 반환됩니다. 메트릭에 저장된 값은 `CLSID` COM 함수에 `CoCreateInstance` 전달되는 값입니다(예제 참조).

디버깅 기능을 `SetEEMetric` [위한 SDK 도우미는](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 사용자 지정 뷰어를 등록하는 데 사용할 수 있습니다. 사용자 지정 뷰어가 필요로 하는 `Debugging SDK Helpers` 특정 레지스트리 키에 대한 "표현식 평가자" 레지스트리 섹션을 참조하십시오. 사용자 지정 뷰어에는 EE 구현자가 정의한 메트릭이 하나만 필요하지만 식 계산기에는 미리 정의된 여러 메트릭이 필요합니다.

일반적으로 사용자 지정 뷰어는 [DisplayValue에](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) 제공된 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스에 문자열을 제외한 속성 값을 변경하는 메서드가 없으므로 데이터에 대한 읽기 전용 보기를 제공합니다. 변경되는 임의의 데이터 블록을 지원하기 위해 EE는 `IDebugProperty3` 인터페이스를 구현하는 동일한 개체에 사용자 지정 인터페이스를 구현합니다. 그런 다음 이 사용자 지정 인터페이스는 임의의 데이터 블록을 변경하는 데 필요한 메서드를 제공합니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="example"></a>예제
이 예제에서는 해당 속성에 사용자 지정 뷰어가 있는 경우 속성에서 첫 번째 사용자 지정 뷰어를 얻는 방법을 보여 주어집니다.

```cpp
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

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [디버깅을 위한 SDK 도우미](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)

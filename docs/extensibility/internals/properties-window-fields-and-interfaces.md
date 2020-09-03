---
title: 속성 창 필드 및 인터페이스 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9529708c781e7fdb04c3b4c5ee143b7605857e84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706158"
---
# <a name="properties-window-fields-and-interfaces"></a>Properties Window Fields and Interfaces
**속성** 창에 표시 되는 정보를 결정 하기 위해 선택할 수 있는 모델은 IDE에 포커스가 있는 창을 기반으로 합니다. 모든 창 및 선택한 창 내의 개체는 선택 컨텍스트 개체를 전역 선택 컨텍스트로 푸시할 수 있습니다. 환경에서는 해당 창에 포커스가 있을 때 창 프레임의 값으로 전역 선택 컨텍스트를 업데이트 합니다. 포커스가 변경 되 면 선택 컨텍스트가 수행 됩니다.

## <a name="tracking-selection-in-the-ide"></a>IDE에서 선택 추적
 IDE에서 소유 하는 창 프레임이 나 사이트에는 라는 서비스가 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . 다음 단계에서는 사용자가 다른 열린 창으로 포커스를 변경 하거나 **솔루션 탐색기**에서 다른 프로젝트 항목을 선택 하 여 **속성** 창에 표시 되는 내용을 변경 하는 등의 선택 변경 작업을 수행 하는 방법을 보여 줍니다.

1. 선택한 창에 배치 되는 VSPackage에서 만든 개체는 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> 를 호출 하 여를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> 합니다.

2. 선택한 창에서 제공 하는 선택 컨테이너는 해당 개체를 만듭니다 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> . 선택이 변경 되 면 VSPackage는를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 하 여 **속성** 창을 포함 하 여 환경의 수신기에 변경 내용을 알립니다. 또한 새 선택 영역과 관련 된 계층 및 항목 정보에 대 한 액세스를 제공 합니다.

3. <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>을 호출 하 고 전달 하면 매개 변수에서 선택한 계층 항목이 `VSHPROPID_BrowseObject` 개체를 채웁니다 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .

4. [IDispatch 인터페이스](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) 에서 파생 된 개체는 __VSHPROPID에 대해 반환 됩니다 [. ](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>)요청 된 항목에 대 한 VSHPROPID_BrowseObject 하 고 환경에서로 래핑합니다 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (다음 단계 참조). 호출이 실패 하면 환경에서에 대 한 두 번째 호출을 수행 하 여 `IVsHierarchy::GetProperty` 선택 컨테이너 [__VSHPROPID 전달 합니다. ](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) 계층 항목 또는 항목이 제공 하는 VSHPROPID_SelContainer 합니다.

    VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 을 구현 하는 환경 제공 창 VSPackage (예: **솔루션 탐색기**)가 대신 생성 되기 때문에 프로젝트를 만들 수 없습니다 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .

5. 환경에서는의 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 하 여 `IDispatch` **속성** 창에 채울 인터페이스를 기반으로 개체를 가져옵니다.

   **속성** 창의 값이 변경 되 면 vspackage를 구현 하 여 `IVsTrackSelectionEx::OnElementValueChangeEx` `IVsTrackSelectionEx::OnSelectionChangeEx` 요소 값에 대 한 변경 내용을 보고 합니다. 그러면 환경에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 또는를 호출 하 여 속성 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> 창에 표시 **Properties** 되는 정보를 속성 값과 동기화 된 상태로 유지 합니다. 자세한 내용은 [속성 창에서 속성 값 업데이트](#updating-property-values-in-the-properties-window)를 참조 하세요.

   **솔루션 탐색기** 에서 다른 프로젝트 항목을 선택 하 여 해당 항목과 관련 된 속성을 표시 하는 것 외에도 **속성** 창에서 사용할 수 있는 드롭다운 목록을 사용 하 여 양식 또는 문서 창 내에서 다른 개체를 선택할 수 있습니다. 자세한 내용은 [속성 창 개체 목록](../../extensibility/internals/properties-window-object-list.md)을 참조 하세요.

   **속성** 창 표에 정보를 표시 하는 방법을 사전순에서 범주별로 변경 하 고, 사용 가능한 경우 **속성** 창에서 해당 단추를 클릭 하 여 선택한 개체에 대 한 속성 페이지를 열 수도 있습니다. 자세한 내용은 [속성 창 단추](../../extensibility/internals/properties-window-buttons.md) 및 [속성 페이지](../../extensibility/internals/property-pages.md)를 참조 하세요.

   마지막으로 **속성** 창의 아래쪽에는 **속성** 창 표에서 선택한 필드에 대 한 설명도 포함 됩니다. 자세한 내용은 [속성 창에서 필드 설명 가져오기](#getting-field-descriptions-from-the-properties-window)를 참조 하세요.

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a> 속성 창에서 속성 값 업데이트
**속성** 창이 속성 값 변경과 동기화 상태를 유지하도록 하는 방법에는 두 가지가 있습니다. 첫 번째는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 인터페이스를 호출하는 방법입니다. 이 인터페이스는 환경에서 제공하는 도구 및 문서 창의 생성 및 액세스를 포함한 기본적인 창 관리 기능에 대한 액세스를 제공합니다. 다음 단계에서 이 동기화 프로세스를 설명합니다.

### <a name="updating-property-values-using-ivsuishell"></a>IVsUIShell을 사용하여 속성 값 업데이트

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>IVsUIShell 인터페이스를 사용하여 속성 값을 업데이트하려면

1. VSPackages, 프로젝트 또는 편집기가 도구 또는 문서 창을 만들거나 열거해야 할 때 언제라도 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>을 호출합니다(<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 서비스를 통해).

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A>이벤트를 구현 하 고 발생 시 키 지 않고 프로젝트 (또는 **속성** 창에서 탐색 하는 다른 모든 선택 된 개체)에 대 한 속성 변경 내용과 **속성** 창을 동기화 된 상태로 유지 하려면 구현 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> 합니다.

3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 메서드 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A>를 구현하여 계층이 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>를 구현할 필요 없이 계층  이벤트의 클라이언트 알림을 설정 및 비활성화합니다.

### <a name="updating-property-values-using-iconnection"></a>IConnection을 사용하여 속성 값 업데이트
 **속성** 창과 속성 값 변경의 동기화를 유지하는 두 번째 방법은 연결 가능 개체에 `IConnection` 를 구현하여 송신 인터페이스가 있음을 나타내는 것입니다. 속성 이름을 지역화하려는 경우에는 <xref:System.ComponentModel.ICustomTypeDescriptor>에서 개체를 파생하세요. <xref:System.ComponentModel.ICustomTypeDescriptor> 구현은 반환되는 속성 설명자를 수정하고 속성의 이름을 변경할 수 있습니다. 설명을 지역화하려면 <xref:System.ComponentModel.DescriptionAttribute>에서 파생되는 특성을 만들고 설명 속성을 재정의하세요.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>IConnection 인터페이스 구현 시 고려 사항

1. `IConnection`는 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> 인터페이스를 통해 열거자 하위 개체에 대한 액세스를 제공합니다. 또한 각각 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 인터페이스를 구현하는 모든 연결점 하위 개체에 대한 액세스도 제공합니다.

2. 모든 찾아보기 개체가 <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> 이벤트 구현을 담당합니다. **속성** 창은 `IConnection`를 통해 설정된 이벤트에 대해 통지합니다.

3. 연결점은 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>의 구현에서 허용되는 연결 수(하나 또는 그 이상)를 제어합니다. 하나의 인터페이스만 허용하는 연결점은 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> 메서드에서 <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>을 반환할 수 있습니다.

4. 클라이언트는 `IConnection` 인터페이스를 호출하여 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> 인터페이스를 통해 열거자 하위 개체에 대한 액세스를 얻습니다. 그러면 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> 인터페이스를 호출하여 각 송신 인터페이스 ID(IID)에 대한 연결점을 열거할 수 있습니다.

5. 또한 `IConnection`를 호출하여 각 송신 IID에 대한 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 인터페이스를 통해 연결점 하위 개체에 대한 액세스를 얻을 수도 있습니다. 클라이언트는 인터페이스를 통해 연결 가능 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 개체 및 클라이언트의 자체 동기화를 사용 하 여 advise 루프를 시작 하거나 종료 합니다. 클라이언트는 인터페이스를 호출 하 여 인터페이스를 사용 하 여 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 열거자 개체를 가져와 해당 개체가 인식 하는 연결을 열거할 수도 있습니다 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> .

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a> 속성 창에서 필드 설명 가져오기
**속성** 창 맨 아래 설명 영역에는 선택한 속성 필드와 관련된 정보가 표시됩니다. 이 기능은 기본적으로 켜져 있습니다. 설명 필드를 숨기려면 **속성** 창을 오른쪽 단추로 클릭하고 **설명**을 클릭합니다. 그러면 메뉴 창에서 **설명** 제목 옆의 확인 표시가 사라집니다. 같은 방법으로 **설명** 을 다시 토글하면 필드가 표시됩니다.

 설명 필드의 정보는 <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>에서 가져옵니다. 각 메서드, 인터페이스, coclass 등은 형식 라이브러리에 지역화되지 않은 `helpstring` 특성을 가질 수 있습니다. **속성** 창은에서 문자열을 검색 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A> .

### <a name="to-specify-localized-help-strings"></a>지역화된 도움말 문자열을 지정하려면

1. 형식 라이브러리( `helpstringdll` )의 라이브러리 문에`typelib`특성을 추가합니다.

   > [!NOTE]
   > 형식 라이브러리가 개체 라이브러리 (.olb) 파일인 경우 이 단계는 선택 사항입니다.

2. 문자열에 대한 지정 `helpstringcontext` 특성을 지정합니다. `helpstring` 특성을 지정할 수도 있습니다.

    이러한 특성은 실제 .chm 파일 도움말 항목에 포함된 `helpfile` 및 `helpcontext` 특성과 별개입니다.

   강조 표시 된 속성 이름에 대해 표시 될 설명 정보를 검색 하기 위해 **속성** 창은 선택 된 속성에 대해를 호출 하 여 <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> `lcid` 출력 문자열에 대해 원하는 특성을 지정 합니다. 내부적으로 <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2>이(가) `helpstringdll` 특성에 지정된 .dll 파일을 찾아서 지정된 컨텍스트 및 `lcid` 특성으로 이 .dll 파일에 대해 `DLLGetDocumentation`을(를) 호출합니다.

   `DLLGetDocumentation` 의 서명 및 구현:

```cpp
STDAPI DLLGetDocumentation
(
   ITypeLib * /* ptlib */,
   ITypeInfo * /* ptinfo */,
   LCID /* lcid */,
   DWORD dwCtx,
   BSTR * pbstrHelpString
);
```

 `DLLGetDocumentation` 함수는 DLL에 대한.def 파일에 정의된 내보내기여야 합니다.

 내부적으로 .olb 파일이 생성되는데 실제로 이것은 DLL입니다. 이 DLL에는 형식 라이브러리(.tlb) 파일 리소스 하나와 내보내기 함수 `DLLGetDocumentation`하나가 있습니다.

 .olb 파일의 경우 .tlb 파일 자체를 포함하는 것과 같은 파일이므로 `helpstringdll` 특성은 선택 사항입니다.

 따라서 **설명** 창에 문자열이 나타나도록 하려면 최소한 형식 라이브러리에서 `helpstring` 특성을 지정해야 합니다. 이러한 문자열을 지역화하려면 `helpstringdll` (선택 사항) 특성 및 `helpstringcontext` (필수) 특성을 지정하고 `DLLGetDocumentation`을(를) 구현해야 합니다.

 idl의 `helpstringcontext` 특성 및 `DLLGetDocumentation`을(를) 통해 지역화된 정보를 가져올 경우 추가 인터페이스를 구현할 필요가 없습니다.

 속성의 지역화된 이름 및 설명을 가져오는 또 하나의 방법은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A> 구현입니다. 이 방법으로 구현하는 자세한 내용은 [Properties Window Fields and Interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md)에서 참조하세요.

## <a name="see-also"></a>추가 정보

- [속성 확장](../../extensibility/internals/extending-properties.md)

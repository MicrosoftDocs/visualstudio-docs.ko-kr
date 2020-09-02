---
title: 속성 창 필드 및 인터페이스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b58314d64536ecf33cc5589609ee5524a9352629
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700817"
---
# <a name="properties-window-fields-and-interfaces"></a>Properties Window Fields and Interfaces
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**속성** 창에 표시 되는 정보를 결정 하기 위해 선택할 수 있는 모델은 IDE에 포커스가 있는 창을 기반으로 합니다. 모든 창 및 선택한 창 내의 개체는 선택 컨텍스트 개체를 전역 선택 컨텍스트로 푸시할 수 있습니다. 환경에서는 해당 창에 포커스가 있을 때 창 프레임의 값으로 전역 선택 컨텍스트를 업데이트 합니다. 포커스가 변경 되 면 선택 컨텍스트가 수행 됩니다.  
  
## <a name="tracking-selection-in-the-ide"></a>IDE에서 선택 추적  
 IDE에서 소유 하는 창 프레임이 나 사이트에는 라는 서비스가 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . 다음 단계에서는 사용자가 다른 열린 창으로 포커스를 변경 하거나 **솔루션 탐색기**에서 다른 프로젝트 항목을 선택 하 여 **속성** 창에 표시 되는 내용을 변경 하는 등의 선택 변경 작업을 수행 하는 방법을 보여 줍니다.  
  
1. 선택한 창에 배치 되는 VSPackage에서 만든 개체는 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> 를 호출 하 여를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> 합니다.  
  
2. 선택한 창에서 제공 하는 선택 컨테이너는 해당 개체를 만듭니다 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> . 선택이 변경 되 면 VSPackage는를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 하 여 **속성** 창을 포함 하 여 환경의 수신기에 변경 내용을 알립니다. 또한 새 선택 영역과 관련 된 계층 및 항목 정보에 대 한 액세스를 제공 합니다.  
  
3. <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>을 호출 하 고 전달 하면 매개 변수에서 선택한 계층 항목이 `VSHPROPID_BrowseObject` 개체를 채웁니다 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .  
  
4. [IDispatch 인터페이스](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) 에서 파생 된 개체는 요청 된 항목에 대해 반환 되 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> 고 환경에서는로 래핑 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (다음 단계 참조). 호출이 실패 하면 환경에서에 대 한 두 번째 호출을 수행 하 여 `IVsHierarchy::GetProperty` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> 계층 항목이 제공 하는 선택 컨테이너를 전달 합니다.  
  
    VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 을 구현 하는 환경 제공 창 VSPackage (예: **솔루션 탐색기**)가 대신 생성 되기 때문에 프로젝트를 만들 수 없습니다 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .  
  
5. 환경에서는의 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 하 여 `IDispatch` **속성** 창에 채울 인터페이스를 기반으로 개체를 가져옵니다.  
  
   **속성** 창의 값이 변경 되 면 vspackage를 구현 하 여 `IVsTrackSelectionEx::OnElementValueChangeEx` `IVsTrackSelectionEx::OnSelectionChangeEx` 요소 값에 대 한 변경 내용을 보고 합니다. 그러면 환경에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 또는를 호출 하 여 속성 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> 창에 표시 **Properties** 되는 정보를 속성 값과 동기화 된 상태로 유지 합니다. 자세한 내용은 [속성 창에서 속성 값 업데이트](../../misc/updating-property-values-in-the-properties-window.md)를 참조 하세요.  
  
   **솔루션 탐색기** 에서 다른 프로젝트 항목을 선택 하 여 해당 항목과 관련 된 속성을 표시 하는 것 외에도 **속성** 창에서 사용할 수 있는 드롭다운 목록을 사용 하 여 양식 또는 문서 창 내에서 다른 개체를 선택할 수 있습니다. 자세한 내용은 [속성 창 개체 목록](../../extensibility/internals/properties-window-object-list.md)을 참조 하세요.  
  
   **속성** 창 표에 정보를 표시 하는 방법을 사전순에서 범주별로 변경 하 고, 사용 가능한 경우 **속성** 창에서 해당 단추를 클릭 하 여 선택한 개체에 대 한 속성 페이지를 열 수도 있습니다. 자세한 내용은 [속성 창 단추](../../extensibility/internals/properties-window-buttons.md) 및 [속성 페이지](../../extensibility/internals/property-pages.md)를 참조 하세요.  
  
   마지막으로 **속성** 창의 아래쪽에는 **속성** 창 표에서 선택한 필드에 대 한 설명도 포함 됩니다. 자세한 내용은 [속성 창에서 필드 설명 가져오기](../../misc/getting-field-descriptions-from-the-properties-window.md)를 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [속성 확장](../../extensibility/internals/extending-properties.md)

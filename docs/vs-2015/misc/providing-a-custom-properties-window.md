---
title: 사용자 지정 속성 창 제공 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- property browsers, providing
- Properties window, providing your own
ms.assetid: 408dcdef-8ef9-4644-97d2-f311cd35824f
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: a244463832ff5620efa74a2c7fd20d6d47d79e76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62810706"
---
# <a name="providing-a-custom-properties-window"></a>사용자 지정 속성 창 제공
IDE (통합 개발 환경)에서 제공 하는 **속성** 창을 확장 하는 대신 지정 된 프로젝트 시스템에 대 한 고유한 **속성** 창을 제공할 수 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . 가장 자주 발생 하는 시나리오는 창 프레임에 배치 된 개체를 직접 구현 하는 경우입니다.  
  
 창 프레임에 배치 된 개체는 구현 하지 않지만 다른 방법으로도 액세스할 수 있는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 이 페이지의 마지막 절차에 나열 된 대로 인터페이스에 액세스 하는 여러 가지 방법이 있습니다.  
  
### <a name="to-provide-your-properties-window"></a>속성 창을 제공 하려면  
  
1. **속성** 창 구현을 나타내는 GUID를 정의 합니다.  
  
2. 구현에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 서비스를 사용 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> 하 여 **속성** 창을 Visual Studio 환경에 서비스로 proffer.  
  
### <a name="to-call-your-properties-window"></a>속성 창을 호출 하려면  
  
1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> 메서드를 호출합니다.  
  
2. `QueryService`<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>메서드에 전달 된에서에 대 한입니다 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> .  
  
3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>서비스에서 가져옵니다 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> .  
  
4. <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>첫 번째 매개 변수를 (열거형에서 사용)로 설정 하 고 세 번째 매개 변수를 사용 하 여를 호출 `SEID_PropertyBrowserSID` <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> 합니다 .이 매개 변수는 `varValue` **속성** 창을 나타내는 GUID의 문자열 형식을 나타냅니다. **속성** 창 문서 창을 처음 만들 때 한 번만이 호출을 수행 합니다. 호출 후에이 **속성** 창이 창 프레임에 연결 됩니다.  
  
### <a name="to-obtain-the-window-frame-object-when-you-are-not-the-implementer"></a>구현 자가 아닌 경우 창 프레임 개체를 가져오려면  
  
- `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 매개 변수를로 설정 하 여의 서비스 `propid` <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> 를 사용할 수 있습니다.  
  
- SVsMonitorSelection 서비스를 통해를 호출 하 여 활성 문서 창을 가져올 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> . `elementid`열거형에서 가져온 매개 변수를로 설정 합니다 `SEID_WindowFrame` <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> .  
  
## <a name="see-also"></a>관련 항목  
 [속성 확장](../extensibility/internals/extending-properties.md)   
 [Properties Window Fields and Interfaces](../extensibility/internals/properties-window-fields-and-interfaces.md)
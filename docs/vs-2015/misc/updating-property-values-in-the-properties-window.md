---
title: 속성 창에서 속성 값 업데이트 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Properties window, updating property values
- property values, updating in Properties window
ms.assetid: 9358e8c3-b9d2-4fd4-aaab-cf48d1526db4
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 18ecf0a21c5b2d73bdf8e439d25765b6b275cbd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434191"
---
# <a name="updating-property-values-in-the-properties-window"></a>속성 창에서 속성 값을 업데이트합니다.
**속성** 창이 속성 값 변경과 동기화 상태를 유지하도록 하는 방법에는 두 가지가 있습니다. 첫 번째는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 인터페이스를 호출하는 방법입니다. 이 인터페이스는 환경에서 제공하는 도구 및 문서 창의 생성 및 액세스를 포함한 기본적인 창 관리 기능에 대한 액세스를 제공합니다. 다음 단계에서 이 동기화 프로세스를 설명합니다.  
  
## <a name="updating-property-values-using-ivsuishell"></a>IVsUIShell을 사용하여 속성 값 업데이트  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>IVsUIShell 인터페이스를 사용하여 속성 값을 업데이트하려면  
  
1. VSPackages, 프로젝트 또는 편집기가 도구 또는 문서 창을 만들거나 열거해야 할 때 언제라도 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>을 호출합니다(<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 서비스를 통해).  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A>이벤트를 구현 하 고 발생 시 키 지 않고 프로젝트 (또는 **속성** 창에서 탐색 하는 다른 모든 선택 된 개체)에 대 한 속성 변경 내용과 **속성** 창을 동기화 된 상태로 유지 하려면 구현 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> 합니다.  
  
3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 메서드 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A>를 구현하여 계층이 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>를 구현할 필요 없이 계층  이벤트의 클라이언트 알림을 설정 및 비활성화합니다.  
  
## <a name="updating-property-values-using-iconnection"></a>IConnection을 사용하여 속성 값 업데이트  
 **속성** 창과 속성 값 변경의 동기화를 유지하는 두 번째 방법은 연결 가능 개체에 `IConnection` 를 구현하여 송신 인터페이스가 있음을 나타내는 것입니다. 속성 이름을 지역화하려는 경우에는 <xref:System.ComponentModel.ICustomTypeDescriptor>에서 개체를 파생하세요. <xref:System.ComponentModel.ICustomTypeDescriptor> 구현은 반환되는 속성 설명자를 수정하고 속성의 이름을 변경할 수 있습니다. 설명을 지역화하려면 <xref:System.ComponentModel.DescriptionAttribute>에서 파생되는 특성을 만들고 설명 속성을 재정의하세요.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>IConnection 인터페이스 구현 시 고려 사항  
  
1. `IConnection`는 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> 인터페이스를 통해 열거자 하위 개체에 대한 액세스를 제공합니다. 또한 각각 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 인터페이스를 구현하는 모든 연결점 하위 개체에 대한 액세스도 제공합니다.  
  
2. 모든 찾아보기 개체가 <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> 이벤트 구현을 담당합니다. **속성** 창은 `IConnection`를 통해 설정된 이벤트에 대해 통지합니다.  
  
3. 연결점은 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>의 구현에서 허용되는 연결 수(하나 또는 그 이상)를 제어합니다. 하나의 인터페이스만 허용하는 연결점은 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> 메서드에서 <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>을 반환할 수 있습니다.  
  
4. 클라이언트는 `IConnection` 인터페이스를 호출하여 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> 인터페이스를 통해 열거자 하위 개체에 대한 액세스를 얻습니다. 그러면 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> 인터페이스를 호출하여 각 송신 인터페이스 ID(IID)에 대한 연결점을 열거할 수 있습니다.  
  
5. 또한 `IConnection`를 호출하여 각 송신 IID에 대한 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 인터페이스를 통해 연결점 하위 개체에 대한 액세스를 얻을 수도 있습니다. 클라이언트는 인터페이스를 통해 연결 가능 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 개체 및 클라이언트의 자체 동기화를 사용 하 여 advise 루프를 시작 하거나 종료 합니다. 클라이언트는 인터페이스를 호출 하 여 인터페이스를 사용 하 여 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 열거자 개체를 가져와 해당 개체가 인식 하는 연결을 열거할 수도 있습니다 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> .  
  
## <a name="see-also"></a>관련 항목  
 [속성 창 선택 항목 추적 발표](../misc/announcing-property-window-selection-tracking.md)   
 [속성 확장](../extensibility/internals/extending-properties.md)
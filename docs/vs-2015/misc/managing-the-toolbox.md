---
title: 도구 상자 관리 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Toolbox [Visual Studio SDK], automatic tab selection
- Toolbox [Visual Studio SDK], managing
ms.assetid: 3b052047-f6db-46dd-b3bf-da1c348ee410
caps.latest.revision: 33
manager: jillfra
ms.openlocfilehash: 5eeb5d06b0e689391f450fec8744fa58a41f4508
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681535"
---
# <a name="managing-the-toolbox"></a>Managing the Toolbox
[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 에서는 편집기 또는 디자이너와 같은 VSPackage로 **도구 상자**의 멤버 자격과 모양을 관리할 수 있습니다.  
  
 또한 **도구 상자** 자체는 자동화를 사용하여 관리할 수 있습니다. 자동화를 통해 도구 상자를 관리하는 방법에 대한 자세한 내용은 [How to: Control the Toolbox](https://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599)를 참조하세요.  
  
## <a name="automatic-toolbox-tab-selection"></a>자동 도구 상자 탭 선택  
 현재 활성화된 편집기 또는 디자이너에 따라 특정 **도구 상자** 탭 또는 범주를 자동으로 활성화할 수 있습니다. 예를 들어 폼 디자이너가 활성화된 경우 **모든 Windows Forms** 탭이 선택되도록 할 수 있습니다.  
  
 이 지원은 다음이 필요한 편집기 및 디자이너로 제한됩니다.  
  
1. 편집기 또는 디자이너의 인스턴스를 제공하는 팩터리 개체 구현. 디자이너 또는 편집기 팩터리 개체를 구현하는 방법에 대한 자세한 내용은 [Editor Factories](../extensibility/editor-factories.md)를 참조하세요.  
  
2. 편집기 또는 디자이너가 있으면 자동으로 활성화되는 도구 상자 탭 등록.  
  
## <a name="controlling-the-toolbox"></a>도구 상자 제어  
 자동화 지원을 보완하기 위해 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 에서는 VSPackage가 **도구 상자** 의 관리 방법을 보다 완벽하게 제어할 수 있도록 하는 다음 인터페이스를 제공됩니다.  
  
|인터페이스|설명|  
|---------------|-----------------|  
|<xref:System.Drawing.Design.IToolboxService>|응용 프로그램이 <xref:System.Drawing.Design.ToolboxItem> **도구 상자**에서 개체를 관리, 추가 및 제거할 수 있도록 합니다. 또한 모양과 **도구 상자** 범주를 구성할 수 있도록 합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>|애플리케이션이 활성 기반 **도구 상자** 컨트롤을 관리, 추가 및 제거하고 **도구 상자** 범주와 모양을 구성할 수 있도록 합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>|지속성 및 지역화를 완벽하게 지원하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>에 있는 기능을 확장합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox4>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox5>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox6>||  
  
 이러한 인터페이스로 작업할 때는 다음 몇 가지 중요한 사항에 유의하세요.  
  
- <xref:System.Drawing.Design.IToolboxService>는 관리되는 패키지 프레임워크 기반 VSPackage에서만 사용할 수 있습니다.  
  
- 를 사용 하 여 컨트롤을 **도구 상자** 에 직접 추가할 수 없습니다 <xref:System.Drawing.Design.IToolboxService> .  
  
- VSPackage는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>를 사용하여 컨트롤을 추가하거나, <xref:System.Windows.Forms.AxHost>에서 파생된 래퍼 컨트롤에 해당 컨트롤을 호스트해야 합니다.  
  
   Visual Studio은 <xref:System.Windows.Forms.AxHost>에서 파생된 컨트롤에 ActiveX 컨트롤 래핑을 자동화하기 위한 `Aximp.exe` 도구를 제공합니다. 자세한 내용은 [Aximp.exe (Windows Forms ActiveX 컨트롤 가져오기)](https://msdn.microsoft.com/library/482c0d83-7144-4497-b626-87d2351b78d0)를 참조 하세요.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>는 interop 어셈블리를 통해 사용할 수 있는 COM 기반 인터페이스입니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>에서 파생되며 해당 메서드를 모두 구현합니다.  
  
   개체는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>의 인스턴스만 가져옵니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>에서 파생되지 않으며 해당 메서드를 구현하지도 않습니다.  
  
   두 인터페이스의 기능이 필요한 개체는 환경에서 두 인터페이스의 인스턴스를 모두 가져와야 합니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>으로 작업할 때 탭의 정식(지역화되지 않은) 이름에 대한 정보는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.GetIDOfTab%2A> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.SetIDOfTab%2A> 메서드에 의해 처리됩니다.  
  
- <xref:System.Drawing.Design.IToolboxService>를 사용하는 경우 범주 이름 등의 지역화된 정보를 관리하는 것은 구현자의 책임입니다.  
  
  설정 메커니즘을 사용하여 IDE의 **도구** 메뉴에 있는 **설정 가져오기/내보내기** 명령에서 사용자가 액세스하는 **도구 상자** 설정을 저장할 수 있습니다. 설정을 사용하는 방법에 대한 자세한 내용은 [Extending User Settings and Options](../extensibility/extending-user-settings-and-options.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [도구 상자 확장](../misc/extending-the-toolbox.md)
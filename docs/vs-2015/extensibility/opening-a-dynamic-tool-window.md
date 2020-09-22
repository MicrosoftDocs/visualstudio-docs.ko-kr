---
title: 동적 도구 창 열기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09b81294abc708cf7616dad03b5dd7333d6a1719
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841963"
---
# <a name="opening-a-dynamic-tool-window"></a>동적 도구 창 열기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

도구 창은 일반적으로 메뉴의 명령 또는 해당 하는 바로 가기 키에서 열립니다. 그러나 때때로 특정 UI 컨텍스트가 적용 될 때마다 열리는 도구 창이 필요할 수 있으며 UI 컨텍스트가 더 이상 적용 되지 않는 경우 닫힙니다. 이러한 도구 창을 *동적* 또는 *자동 표시*라고 합니다.  
  
> [!NOTE]
> 미리 정의 된 UI 컨텍스트 목록은를 참조 하십시오 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> . 관리자가  
  
 시작할 때 동적 도구 창을 열고 오류가 발생할 수 있는 경우에는 인터페이스를 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> 하 고 메서드에서 오류 조건을 테스트 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> . 셸에서 시작할 때 열어야 하는 동적 도구 창이 있음을 알려면 `SupportsDynamicToolOwner` 패키지 등록에 값 (1로 설정)을 추가 해야 합니다. 이 값은 표준에 속하지 않으므로 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 사용자 지정 특성을 만들어 추가 해야 합니다. 사용자 지정 특성에 대 한 자세한 내용은 [사용자 지정 등록 특성을 사용 하 여 확장 등록](../misc/using-a-custom-registration-attribute-to-register-an-extension.md)을 참조 하세요.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>를 사용 하 여 도구 창을 엽니다. 필요에 따라 도구 창이 만들어집니다.  
  
> [!NOTE]
> 사용자가 동적 도구 창을 닫을 수 있습니다. 사용자가 도구 창을 다시 열 수 있도록 메뉴 명령을 만들려면 도구 창을 여는 것과 동일한 UI 컨텍스트에서 메뉴 명령을 사용 하도록 설정 하 고 그렇지 않으면 사용 하지 않도록 설정 해야 합니다.  
  
### <a name="to-open-a-dynamic-tool-window"></a>동적 도구 창을 열려면  
  
1. **DynamicToolWindow** 라는 VSIX 프로젝트를 만들고 **DynamicWindowPane.cs**라는 도구 창 항목 템플릿을 추가 합니다. 자세한 내용은 [도구 창을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-tool-window.md)를 참조 하세요.  
  
2. DynamicWindowPanePackage.cs 파일에서 DynamicWindowPanePackage 선언을 찾습니다. <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>및 T:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute 특성을 추가 하 여 도구 창을 등록 합니다.  
  
    ```vb  
    [[ProvideToolWindow(typeof(DynamicWindowPane)]  
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]  
    [Guid(DynamicWindowPanePackageGuids.PackageGuidString)]  
    public sealed class DynamicWindowPanePackage : Package  
    {. . .}  
    ```  
  
     그러면 DynamicWindowPane 라는 도구 창이 Visual Studio를 닫았다가 다시 열 때 유지 되지 않는 임시 창으로 등록 됩니다. DynamicWindowPane는가 적용 될 때마다 열리고 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> 그렇지 않은 경우 닫힙니다.  
  
3. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 표시 되어야 합니다. 도구 창이 표시 되어서는 안 됩니다.  
  
4. 실험적 인스턴스에서 프로젝트를 엽니다. 도구 창이 표시 됩니다.

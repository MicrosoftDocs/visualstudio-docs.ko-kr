---
title: 동적 도구 창 열기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff971f980b0a9b2fb0e22f56fb0ace752829c2c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702254"
---
# <a name="open-a-dynamic-tool-window"></a>동적 도구 창 열기
도구 창은 일반적으로 메뉴의 명령또는 이에 상응하는 키보드 단축구에서 열립니다. 그러나 때로는 특정 UI 컨텍스트가 적용될 때마다 열리고 UI 컨텍스트가 더 이상 적용되지 않을 때 닫히는 도구 창이 필요할 수 있습니다. 이러한 유형의 도구 창은 *동적* 또는 *자동 표시라고*합니다.

> [!NOTE]
> 미리 정의된 UI 컨텍스트 목록은 을 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>참조하십시오.

 시작 시 동적 도구 창을 열고 생성에 실패할 수 있는 경우 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> 구현 하 고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> 메서드에서 실패 조건을 테스트 해야 합니다. 셸에 시작 시 열어야 하는 동적 도구 창이 있음을 알기 위해서는 `SupportsDynamicToolOwner` 패키지 등록에 값(1로 설정)을 추가해야 합니다. 이 값은 표준의 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>일부가 아니므로 추가하려면 사용자 지정 특성을 만들어야 합니다. 사용자 지정 특성에 대한 자세한 내용은 [사용자 지정 등록 특성 사용을 참조하여 확장을 등록합니다.](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension)

 도구 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 창을 여는 데 사용합니다. 필요에 따라 도구 창이 만들어집니다.

> [!NOTE]
> 동적 도구 창을 사용자가 닫을 수 있습니다. 사용자가 도구 창을 다시 열 수 있도록 메뉴 명령을 만들려면 도구 창을 여는 동일한 UI 컨텍스트에서 메뉴 명령을 사용하도록 설정하고 그렇지 않으면 사용하지 않도록 설정해야 합니다.

## <a name="to-open-a-dynamic-tool-window"></a>동적 도구 창을 열려면

1. **DynamicToolWindow라는** VSIX 프로젝트를 만들고 *DynamicWindowPane.cs*라는 도구 창 항목 템플릿을 추가합니다. 자세한 내용은 [도구 창을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-tool-window.md)참조하십시오.

2. *DynamicWindowPanePackage.cs* 파일에서 DynamicWindowPanePackage 선언을 찾습니다. <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> 및 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> 특성을 추가하여 도구 창을 등록합니다.

    ```vb
    [ProvideToolWindow(typeof(DynamicWindowPane)]
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]
    [Guid(DynamicWindowPanePackage.PackageGuidString)]
    public sealed class DynamicWindowPanePackage : Package
    {. . .}
    ```

     위의 특성은 Visual Studio가 닫혀 다시 열릴 때 유지되지 않는 일시적인 창으로 DynamicWindowPane이라는 도구 창을 등록합니다. DynamicWindowPane이 적용될 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> 때마다 열리고 그렇지 않으면 닫힙됩니다.

3. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타나야 합니다. 도구 창이 표시되지 않아야 합니다.

4. 실험 인스턴스에서 프로젝트를 엽니다. 도구 창이 나타납니다.

---
title: 다중 인스턴스 도구 창 만들기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33585f623f846e16200d430ad2c886fe0874b537
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739617"
---
# <a name="create-a-multi-instance-tool-window"></a>다중 인스턴스 도구 창 만들기
도구 창을 프로그래밍하여 여러 인스턴스를 동시에 열 수 있습니다. 기본적으로 도구 창에는 인스턴스가 하나만 열려 있을 수 있습니다.

다중 인스턴스 도구 창을 사용하는 경우 여러 관련 정보 소스를 동시에 표시할 수 있습니다. 예를 들어 다중 인스턴스 도구 <xref:System.Windows.Forms.TextBox> 창에 다중 줄 컨트롤을 배치하여 프로그래밍 세션 중에 여러 코드 조각을 동시에 사용할 수 있습니다. 또한 여러 실시간 데이터 원본을 <xref:System.Windows.Forms.DataGrid> 동시에 추적할 수 있도록 다중 인스턴스 도구 창에 컨트롤및 드롭다운 목록 상자를 넣을 수 있습니다.

## <a name="create-a-basic-single-instance-tool-window"></a>기본(단일 인스턴스) 도구 창 만들기

1. VSIX 템플릿을 사용하여 **MultiInstanceToolWindow라는** 프로젝트를 만들고 **MIToolWindow라는**사용자 지정 도구 창 항목 템플릿을 추가합니다.

    > [!NOTE]
    > 도구 창을 사용하여 확장을 만드는 자세한 내용은 [도구 창을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-tool-window.md)참조하십시오.

## <a name="make-a-tool-window-multi-instance"></a>도구 창 다중 인스턴스 만들기

1. *MIToolWindowPackage.cs* 파일을 열고 특성을 찾습니다. `ProvideToolWindow` 다음 `MultiInstances=true` 예제와 같이 매개 변수를 다음과 같이 표시합니다.

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. *MIToolWindowCommand.cs* 파일에서 메서드를 `ShowToolWindos()` 찾습니다. 이 메서드에서는 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 메서드를 호출 `create` 하고 `false` 사용 가능한 `id` 찾을 때까지 기존 도구 창 인스턴스를 반복 하도록 플래그를 설정 합니다.

3. 도구 창 인스턴스를 만들려면 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 메서드를 `id` 호출하고 해당 메서드를 사용 가능한 값으로 설정하고 해당 `create` 플래그를 로 `true`설정합니다.

    기본적으로 `id` <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 메서드의 매개 변수 값은 `0`은 . 이 값은 단일 인스턴스 도구 창을 만듭니다. 두 개 이상의 인스턴스를 호스트하려면 모든 인스턴스마다 `id`고유한 .

4. 도구 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> 창 인스턴스의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> 속성에서 반환되는 개체의 메서드를 호출합니다.

5. 기본적으로 도구 `ShowToolWindow` 창 항목 템플릿에 의해 만들어진 메서드는 단일 인스턴스 도구 창을 만듭니다. 다음 예제에서는 메서드를 `ShowToolWindow` 수정하여 여러 인스턴스를 만드는 방법을 보여 주며, 이 예제에서는 여러 인스턴스를 만드는 방법을 보여 주며, 이 방법을 보여 주시면 됩니다.

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        for (int i = 0; i < 10; i++)
        {
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);
            if (window == null)
            {
                // Create the window with the first free ID.
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);
                if ((null == window) || (null == window.Frame))
                {
                    throw new NotSupportedException("Cannot create tool window");
                }

            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());
            break;
            }
        }
    }
    ```

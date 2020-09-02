---
title: 다중 인스턴스 도구 창 만들기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1bb84ed9961cac5159e15bc0c45fada5426d2f2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904063"
---
# <a name="create-a-multi-instance-tool-window"></a>다중 인스턴스 도구 창 만들기
여러 인스턴스를 동시에 열 수 있도록 도구 창을 프로그래밍할 수 있습니다. 기본적으로 도구 창에는 인스턴스가 하나만 열려 있을 수 있습니다.

다중 인스턴스 도구 창을 사용 하는 경우 여러 관련 정보 원본을 동시에 표시할 수 있습니다. 예를 들어 여러 <xref:System.Windows.Forms.TextBox> 개의 코드 조각을 프로그래밍 세션 중에 동시에 사용할 수 있도록 다중 인스턴스 도구 창에 여러 줄로 된 컨트롤을 배치할 수 있습니다. 예를 들어 <xref:System.Windows.Forms.DataGrid> 여러 실시간 데이터 원본을 동시에 추적할 수 있도록 다중 인스턴스 도구 창에 컨트롤과 드롭다운 목록 상자를 둘 수 있습니다.

## <a name="create-a-basic-single-instance-tool-window"></a>기본 (단일 인스턴스) 도구 창 만들기

1. VSIX 템플릿을 사용 하 여 **Multiinstancetoolwindow** 라는 프로젝트를 만들고 **MIToolWindow**이라는 사용자 지정 도구 창 항목 템플릿을 추가 합니다.

    > [!NOTE]
    > 도구 창을 사용 하 여 확장을 만드는 방법에 대 한 자세한 내용은 [도구 창을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-tool-window.md)를 참조 하세요.

## <a name="make-a-tool-window-multi-instance"></a>도구 창 다중 인스턴스 만들기

1. *MIToolWindowPackage.cs* 파일을 열고 특성을 찾습니다 `ProvideToolWindow` . `MultiInstances=true`다음 예제와 같이 매개 변수를 및 매개 변수로 표시 합니다.

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. *MIToolWindowCommand.cs* 파일에서 메서드를 찾습니다 `ShowToolWindos()` . 이 메서드에서는 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 하 고, `create` `false` 사용 가능한이 발견 될 때까지 기존 도구 창 인스턴스를 반복 하도록 플래그를로 설정 `id` 합니다.

3. 도구 창 인스턴스를 만들려면 메서드를 호출 하 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 고을 `id` 사용 가능한 값으로 설정 하 고 `create` 플래그를로 설정 `true` 합니다.

    기본적으로 `id` 메서드의 매개 변수 값은 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> `0` 입니다. 이 값은 단일 인스턴스 도구 창을 만듭니다. 둘 이상의 인스턴스가 호스팅될 경우 모든 인스턴스에 고유한가 있어야 합니다 `id` .

4. <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 도구 창 인스턴스의 속성에 의해 반환 되는 개체에서 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> .

5. 기본적으로 `ShowToolWindow` 도구 창 항목 템플릿에서 만든 메서드는 단일 인스턴스 도구 창을 만듭니다. 다음 예제에서는 메서드를 수정 하 여 `ShowToolWindow` 여러 인스턴스를 만드는 방법을 보여 줍니다.

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

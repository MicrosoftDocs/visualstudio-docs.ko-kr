---
title: VS패키지로 확장 만들기 | 마이크로 소프트 문서
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1037ebcc58cc4183e6f02119bc7b46abfc132f52
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739531"
---
# <a name="create-an-extension-with-a-vspackage"></a>VS패키지로 확장 만들기

이 연습에서는 VSIX 프로젝트를 만들고 VSPackage 프로젝트 항목을 추가하는 방법을 보여 주며, 이를 보여 주시면 됩니다. VSPackage를 사용 하 여 UI 셸 서비스를 가져옵니다 메시지 상자를 표시 하기 위해.

## <a name="prerequisites"></a>사전 요구 사항

Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. 시각적 스튜디오 설정에서 선택적 기능으로 포함됩니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-a-vspackage"></a>VS패키지 만들기

1. **FirstPackage라는**VSIX 프로젝트를 만듭니다. 새 프로젝트 대화 상자에서 "vsix"를 검색하여 VSIX **프로젝트** 템플릿을 찾을 수 있습니다.

2. 프로젝트가 열리면 FirstPackage 라는 Visual Studio 패키지 항목 템플릿을 **추가합니다.** 솔루션 **탐색기에서**프로젝트 노드를 마우스 오른쪽 단추로 클릭하고**새 항목** **추가를** > 선택합니다. 새 **항목 추가** 대화 상자에서 **Visual C#** > **확장성으로** 이동하여 **Visual Studio 패키지를**선택합니다. 창 아래쪽의 **이름** 필드에서 명령 파일 이름을 *FirstPackage.cs*.

3. 프로젝트를 빌드하고 디버깅을 시작합니다.

    Visual Studio의 실험 인스턴스가 나타납니다. 실험 인스턴스에 대한 자세한 내용은 [실험 인스턴스 를](../extensibility/the-experimental-instance.md)참조하십시오.

4. 실험 인스턴스에서 **도구** > 확장 및 업데이트 창을**엽니다.** **여기에 FirstPackage** 확장이 표시됩니다. (Visual Studio의 작업 인스턴스에서 **확장 및 업데이트를** 열면 **FirstPackage가**표시되지 않습니다.)

## <a name="load-the-vspackage"></a>VS패키지 로드

이 시점에서 확장로드를 발생 시키는 아무 것도 없기 때문에 확장로드 되지 않습니다. 일반적으로 UI와 상호 작용할 때(메뉴 명령 클릭, 도구 창 열기) 또는 VSPackage가 특정 UI 컨텍스트에서 로드되도록 지정하여 확장을 로드할 수 있습니다. VSPackage 및 UI 컨텍스트 로드에 대한 자세한 내용은 [VSPackage 로드](../extensibility/loading-vspackages.md)를 참조하십시오. 이 절차에서는 솔루션이 열려 있을 때 VSPackage를 로드하는 방법을 보여 드리겠습니다.

1. *FirstPackage.cs* 파일을 엽니다. 클래스의 선언을 `FirstPackage` 찾습니다. 기존 특성을 다음 특성으로 바꿉꿉입니다.

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. VSPackage가 로드되었음을 알려주는 메시지를 추가해 보겠습니다. VSPackage가 사이트를 된 `Initialize()` 후에만 Visual Studio 서비스를 받을 수 있으므로 VSPackage의 메서드를 사용하여 이 작업을 수행합니다. 서비스 가져오는 방법에 대한 자세한 내용은 [서비스 받기 방법을](../extensibility/how-to-get-a-service.md)참조하십시오. <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 메서드를 `Initialize()` `FirstPackage` 서비스를 받고 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 가져옵니다 및 해당 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> 호출하는 코드로 바꿉니다.

    ```csharp
    protected override void Initialize()
    {
        base.Initialize();

        IVsUIShell uiShell = (IVsUIShell)GetService(typeof(SVsUIShell));
        Guid clsid = Guid.Empty;
        int result;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(uiShell.ShowMessageBox(
            0,
            ref clsid,
            "FirstPackage",
             string.Format(CultureInfo.CurrentCulture, "Inside {0}.Initialize()", this.GetType().FullName),
            string.Empty,
            0,
            OLEMSGBUTTON.OLEMSGBUTTON_OK,
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
            OLEMSGICON.OLEMSGICON_INFO,
            0,
            out result));
    }
    ```

3. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타납니다.

4. 실험 인스턴스에서 솔루션을 엽니다. **초기화() 내부에 첫 번째 패키지라는**메시지 상자가 표시됩니다.

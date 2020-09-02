---
title: VSPackage를 사용 하 여 확장 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ddad7149db75aa662f9427a301c04eaf925146f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197427"
---
# <a name="creating-an-extension-with-a-vspackage"></a>VSPackage로 확장 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 VSIX 프로젝트를 만들고 VSPackage 프로젝트 항목을 추가 하는 방법을 보여 줍니다. VSPackage를 사용 하 여 메시지 상자를 표시 하기 위해 UI Shell 서비스를 가져옵니다.  
  
## <a name="prerequisites"></a>사전 준비 사항  
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.  
  
## <a name="creating-a-vspackage"></a>VSPackage 만들기  
  
1. **Firstpackage**라는 VSIX 프로젝트를 만듭니다. **새 프로젝트** 대화 상자의 **Visual c #/확장성**에서 VSIX 프로젝트 템플릿을 찾을 수 있습니다.  
  
2. 프로젝트가 열리면 **firstpackage**라는 Visual Studio 패키지 항목 템플릿을 추가 합니다. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **추가/새 항목**을 선택 합니다. **새 항목 추가** 대화 상자에서 **Visual c #/확장성** 으로 이동 하 고 **visual Studio 패키지**를 선택 합니다. 창 맨 아래에 있는 **이름** 필드에서 명령 파일 이름을 **FirstPackage.cs**로 변경 합니다.  
  
3. 프로젝트를 빌드하고 디버깅을 시작합니다.  
  
     Visual Studio의 실험적 인스턴스가 나타납니다. 실험적 인스턴스에 대 한 자세한 내용은 [실험적 인스턴스](../extensibility/the-experimental-instance.md)를 참조 하세요.  
  
4. 실험적 인스턴스에서 **도구/확장 및 업데이트** 창을 엽니다. 여기에 **Firstpackage** 확장이 표시 됩니다. Visual Studio의 작업 인스턴스에서 **확장 및 업데이트** 를 열면 **firstpackage**가 표시 되지 않습니다.  
  
## <a name="loading-the-vspackage"></a>VSPackage 로드  
 이 시점에서 확장이 로드 되지 않으므로 로드 되지 않습니다. 일반적으로 UI (메뉴 명령 클릭, 도구 창 열기)와 상호 작용 하거나 VSPackage 특정 UI 컨텍스트에서 로드 되도록 지정 하 여 확장을 로드할 수 있습니다. Vspackage 및 UI 컨텍스트를 로드 하는 방법에 대 한 자세한 내용은 [Vspackage 로드](../extensibility/loading-vspackages.md)를 참조 하세요. 이 절차에서는 솔루션이 열려 있을 때 VSPackage를 로드 하는 방법을 보여 줍니다.  
  
1. FirstPackage.cs 파일을 엽니다. FirstPackage 클래스의 선언을 찾습니다. 기존 특성을 다음과 같이 바꿉니다.  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2. VSPackage가 로드 되었음을 알리는 메시지를 추가 해 보겠습니다. VSPackage의 Initialize () 메서드를 사용 하 여이 작업을 수행 합니다. VSPackage가 배치 된 후에만 Visual Studio 서비스를 가져올 수 있기 때문입니다. 서비스를 가져오는 방법에 대 한 자세한 내용은 [방법: 서비스 가져오기](../extensibility/how-to-get-a-service.md)를 참조 하세요. FirstPackage의 Initialize () 메서드를 서비스를 가져오고 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 인터페이스를 가져오고, 해당 메서드를 호출 하는 코드로 바꿉니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> .  
  
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
  
3. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 나타납니다.  
  
4. 실험적 인스턴스에서 솔루션을 엽니다. **Initialize () 내의 첫 번째 패키지**라는 메시지 상자가 표시 됩니다.

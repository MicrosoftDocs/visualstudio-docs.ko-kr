---
title: Vspackage 로드 중 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e20caff476e116ad59430692719bdbbe22c4914c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841699"
---
# <a name="loading-vspackages"></a>VSPackage 로드
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vspackage는 해당 기능이 필요한 경우에만 Visual Studio에 로드 됩니다. 예를 들어 Visual Studio가 프로젝트 팩터리 또는 VSPackage가 구현 하는 서비스를 사용 하는 경우 VSPackage이 로드 됩니다. 이 기능을 사용 하면 성능이 향상 될 때마다 사용 되는 지연 된 로드 라고 합니다.  
  
> [!NOTE]
> Visual Studio는 VSPackage를 로드 하지 않고 VSPackage가 제공 하는 명령과 같은 특정 VSPackage 정보를 결정할 수 있습니다.  
  
 Vspackage는 특정 UI (사용자 인터페이스) 컨텍스트에서 autoload로 설정할 수 있습니다 (예: 솔루션이 열려 있는 경우). <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>특성은이 컨텍스트를 설정 합니다.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>특정 컨텍스트에서 VSPackage 자동 로드  
  
- `ProvideAutoLoad`VSPackage 특성에 특성을 추가 합니다.  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>UI 컨텍스트 및 해당 GUID 값 목록은의 열거 된 필드를 참조 하세요.  
  
- 메서드에 중단점을 설정 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 합니다.  
  
- VSPackage를 빌드하고 디버깅을 시작 합니다.  
  
- 솔루션을 로드 하거나 새로 만듭니다.  
  
     VSPackage가 중단점에서 로드 되 고 중지 됩니다.  
  
## <a name="forcing-a-vspackage-to-load"></a>강제로 VSPackage를 로드 하는 중  
 일부 환경에서는 VSPackage에서 다른 VSPackage을 강제로 로드 해야 할 수도 있습니다. 예를 들어, 경량 VSPackage CMDUIContext로 사용할 수 없는 컨텍스트에서 더 큰 VSPackage을 로드할 수 있습니다.  
  
 메서드를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> VSPackage을 강제로 로드할 수 있습니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>다른 VSPackage을 강제로 로드 하도록 하는 VSPackage의 메서드에이 코드를 삽입 합니다.  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     VSPackage이 초기화 되 면 강제로 `PackageToBeLoaded` 로드 됩니다.  
  
     VSPackage 통신에는 강제 로드를 사용 하면 안 됩니다. 대신 [사용 및 제공 서비스를](../extensibility/using-and-providing-services.md) 사용 합니다.  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>사용자 지정 특성을 사용 하 여 VSPackage 등록  
 특정 한 경우에는 확장에 대 한 새 등록 특성을 만들어야 할 수 있습니다. 등록 특성을 사용 하 여 새 레지스트리 키를 추가 하거나 기존 키에 새 값을 추가할 수 있습니다. 새 특성은에서 파생 되 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> 고 및 메서드를 재정의 해야 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> 합니다 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> .  
  
## <a name="creating-a-registry-key"></a>레지스트리 키 만들기  
 다음 코드에서 사용자 지정 특성은 등록 되는 VSPackage에 대 한 키 아래에 **사용자 지정** 하위 키를 만듭니다.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
  
```  
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>기존 레지스트리 키 아래에 새 값을 만듭니다.  
 기존 키에 사용자 지정 값을 추가할 수 있습니다. 다음 코드에서는 VSPackage 등록 키에 새 값을 추가 하는 방법을 보여 줍니다.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [VSPackages](../extensibility/internals/vspackages.md)

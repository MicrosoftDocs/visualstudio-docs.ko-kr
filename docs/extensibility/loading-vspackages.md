---
title: 로딩 VS패키지 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1c221bf06ef3b7e37e2afc1856f3e54fe5ad95e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702961"
---
# <a name="load-vspackages"></a>로드 VS패키지
VS패키지는 기능이 필요한 경우에만 Visual Studio에 로드됩니다. 예를 들어, VISUAL Studio에서 VSPackage가 구현하는 프로젝트 팩터리 또는 서비스를 사용할 때 VSPackage가 로드됩니다. 이 기능을 지연 된 로드 라고 하며 성능을 향상 시키기 위해 가능 하면 사용 됩니다.

> [!NOTE]
> Visual Studio는 VSPackage를 로드하지 않고 VSPackage가 제공하는 명령과 같은 특정 VSPackage 정보를 확인할 수 있습니다.

 VSPackage는 솔루션이 열려 있는 경우와 같은 특정 사용자 인터페이스(UI) 컨텍스트에서 자동 로드하도록 설정할 수 있습니다. 특성은 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 이 컨텍스트를 설정합니다.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>특정 컨텍스트에서 VSPackage 자동 로드

- VSPackage `ProvideAutoLoad` 특성에 특성을 추가합니다.

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     UI 컨텍스트 및 해당 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> GUID 값의 목록은 나열된 필드를 참조하십시오.

- <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 메서드에서 중단점을 설정합니다.

- VSPackage를 빌드하고 디버깅을 시작합니다.

- 솔루션을 로드하거나 솔루션을 만듭니다.

     VS패키지는 중단점에서 로드되고 중지됩니다.

## <a name="force-a-vspackage-to-load"></a>VS패키지가 로드하도록 강제
 경우에 따라 VSPackage는 다른 VSPackage를 강제로 로드해야 할 수 있습니다. 예를 들어 경량 VSPackage는 CMDUIContext로 사용할 수 없는 컨텍스트에서 더 큰 VSPackage를 로드할 수 있습니다.

 이 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> 사용하여 VSPackage를 강제로 로드할 수 있습니다.

- 이 코드를 VSPackage 메서드에 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 삽입하여 다른 VSPackage를 로드하도록 합니다.

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     VSPackage가 초기화되면 강제로 `PackageToBeLoaded` 로드됩니다.

     VSPackage 통신에는 강제 로딩을 사용할 수 없습니다. 대신 [사용 및 서비스 제공.](../extensibility/using-and-providing-services.md)

## <a name="see-also"></a>참조
- [VSPackage](../extensibility/internals/vspackages.md)

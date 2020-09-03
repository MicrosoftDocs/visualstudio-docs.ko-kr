---
title: Vspackage 로드 중 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702961"
---
# <a name="load-vspackages"></a>Load Vspackage
Vspackage는 해당 기능이 필요한 경우에만 Visual Studio에 로드 됩니다. 예를 들어 Visual Studio가 프로젝트 팩터리 또는 VSPackage가 구현 하는 서비스를 사용 하는 경우 VSPackage이 로드 됩니다. 이 기능을 사용 하면 성능이 향상 될 때마다 사용 되는 지연 된 로드 라고 합니다.

> [!NOTE]
> Visual Studio는 VSPackage를 로드 하지 않고 VSPackage가 제공 하는 명령과 같은 특정 VSPackage 정보를 결정할 수 있습니다.

 Vspackage는 특정 UI (사용자 인터페이스) 컨텍스트에서 autoload로 설정할 수 있습니다 (예: 솔루션이 열려 있는 경우). <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>특성은이 컨텍스트를 설정 합니다.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>특정 컨텍스트에서 VSPackage Autoload

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

## <a name="force-a-vspackage-to-load"></a>강제로 VSPackage 로드
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

     VSPackage 통신에는 강제 로드를 사용 하면 안 됩니다. 대신 [사용 및 서비스 제공을](../extensibility/using-and-providing-services.md) 사용 합니다.

## <a name="see-also"></a>추가 정보
- [VSPackages](../extensibility/internals/vspackages.md)

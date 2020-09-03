---
title: '방법: 서비스 가져오기 | Microsoft Docs'
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a401103112096a1089b59ba3733d19480f93e891
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905826"
---
# <a name="how-to-get-a-service"></a>방법: 서비스 가져오기

다른 기능에 액세스 하려면 Visual Studio 서비스를 받아야 하는 경우가 많습니다. 일반적으로 Visual Studio 서비스는 사용할 수 있는 하나 이상의 인터페이스를 제공 합니다. VSPackage에서 대부분의 서비스를 가져올 수 있습니다.

에서 파생 되 고 올바르게 배치 된 VSPackage는 모든 <xref:Microsoft.VisualStudio.Shell.Package> 전역 서비스를 요청할 수 있습니다. `Package`클래스가을 구현 하기 때문에 <xref:System.IServiceProvider> 에서 파생 되는 모든 VSPackage `Package` 는 서비스 공급자 이기도 합니다.

Visual Studio는를 로드할 때 <xref:Microsoft.VisualStudio.Shell.Package> <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 초기화 하는 동안 개체를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 메서드에 전달 합니다. 이를 VSPackage *사이 팅* 합니다. `Package`클래스는이 서비스 공급자를 래핑하고 서비스를 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 가져오는 메서드를 제공 합니다.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>초기화 된 VSPackage에서 서비스 가져오기

1. 모든 Visual Studio 확장은 확장 자산을 포함 하는 VSIX 배포 프로젝트로 시작 합니다. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]이라는 VSIX 프로젝트를 만듭니다 `GetServiceExtension` . **새 프로젝트** 대화 상자에서 "vsix"를 검색 하 여 vsix 프로젝트 템플릿을 찾을 수 있습니다.

2. 이제 **GetServiceCommand**이라는 사용자 지정 명령 항목 템플릿을 추가 합니다. **새 항목 추가** 대화 상자에서 **Visual c #**  >  **확장성** 으로 이동 하 고 **사용자 지정 명령**을 선택 합니다. 창 맨 아래에 있는 **이름** 필드에서 명령 파일 이름을 *GetServiceCommand.cs*로 변경 합니다. 사용자 지정 명령을 만드는 방법에 대 한 자세한 내용은 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)

3. *GetServiceCommand.cs*에서 메서드의 본문을 제거 `MenuItemCommand` 하 고 다음 코드를 추가 합니다.

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    이 코드는 SVsActivityLog 서비스를 가져오고이를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 작업 로그에 쓰는 데 사용할 수 있는 인터페이스로 캐스팅 합니다. 예제는 [방법: 활동 로그 사용](../extensibility/how-to-use-the-activity-log.md)을 참조 하세요.

4. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 나타납니다.

5. 실험적 인스턴스의 **도구** 메뉴에서 **GetServiceCommand 호출** 단추를 찾습니다. 이 단추를 클릭 하면 **활동 로그 서비스를 찾았습니다** 라는 메시지 상자가 표시 됩니다.

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>도구 창 또는 컨트롤 컨테이너에서 서비스 가져오기

다른 방법으로는 이동 하지 않은 도구 창이 나 제어 컨테이너에서 서비스를 가져와야 하거나, 원하는 서비스를 알지 못하는 서비스 공급자와 함께 서비스를 가져와야 하는 경우도 있습니다. 예를 들어, 컨트롤 내에서 활동 로그에 쓸 수 있습니다.

정적 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 메서드는에서 파생 된 VSPackage가 처음으로 배치 될 때 초기화 되는 캐시 된 서비스 공급자에 의존 합니다 <xref:Microsoft.VisualStudio.Shell.Package> .

VSPackage가 배치 되기 전에 VSPackage 생성자가 호출 되기 때문에 일반적으로 VSPackage 생성자 내에서 전역 서비스를 사용할 수 없습니다. 해결 [방법은 방법: 서비스 문제 해결](../extensibility/how-to-troubleshoot-services.md) 을 참조 하세요.

도구 창 또는 다른 비 VSPackage 요소에서 서비스를 가져오는 방법의 예는 다음과 같습니다.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>DTE 개체에서 서비스 가져오기

개체에서 서비스를 가져올 수도 있습니다 <xref:EnvDTE.DTEClass> . 그러나 VSPackage에서 또는 정적 메서드를 호출 하 여 DTE 개체를 서비스로 가져와야 합니다 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> .

DTE 개체는 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 를 사용 하 여 서비스를 쿼리 하는 데 사용할 수 있는을 구현 합니다 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> .

DTE 개체에서 서비스를 가져오는 방법은 다음과 같습니다.

```csharp
// Start with the DTE object, for example: 
// using EnvDTE;
// DTE dte = (DTE)GetService(typeof(DTE));

ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
if (sp != null)
{
    IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log != null)
    {
        System.Windows.Forms.MessageBox.Show("Found the activity log service.");
    }
}
```

## <a name="see-also"></a>추가 정보

- [방법: 서비스 제공](../extensibility/how-to-provide-a-service.md)
- [사용 및 서비스 제공](../extensibility/using-and-providing-services.md)
- [서비스 essentials](../extensibility/internals/service-essentials.md)

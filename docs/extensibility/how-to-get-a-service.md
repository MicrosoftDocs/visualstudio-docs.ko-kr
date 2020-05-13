---
title: '방법: 서비스 받기 | 마이크로 소프트 문서'
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e8e6f20eaa08d6bb7aaa0cc9e560856daa5959e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710952"
---
# <a name="how-to-get-a-service"></a>방법: 서비스 받기

다양한 기능에 액세스하려면 Visual Studio 서비스를 받아야 하는 경우가 많습니다. 일반적으로 Visual Studio 서비스는 사용할 수 있는 하나 이상의 인터페이스를 제공합니다. VSPackage에서 대부분의 서비스를 받을 수 있습니다.

VSPackage에서 <xref:Microsoft.VisualStudio.Shell.Package> 파생되고 올바르게 사이트된 모든 패키지는 모든 글로벌 서비스를 요청할 수 있습니다. 클래스가 `Package` 구현하기 <xref:System.IServiceProvider>때문에 파생되는 `Package` 모든 VSPackage는 서비스 공급자이기도 합니다.

Visual Studio에서 <xref:Microsoft.VisualStudio.Shell.Package>를 로드하면 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 초기화 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 중에 메서드에 개체를 전달합니다. 이를 VSPackage *를 앉는 이라고* 합니다. 클래스는 `Package` 이 서비스 공급자를 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 래핑하고 서비스를 가져오는 방법을 제공합니다.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>초기화된 VSPackage에서 서비스 받기

1. 모든 Visual Studio 확장은 확장 에셋을 포함하는 VSIX 배포 프로젝트로 시작합니다. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 라는 VSIX 프로젝트를 `GetServiceExtension`만듭니다. 새 프로젝트 대화 상자에서 "vsix"를 검색하여 VSIX **프로젝트** 템플릿을 찾을 수 있습니다.

2. 이제 **GetServiceCommand**이라는 사용자 지정 명령 항목 템플릿을 추가 합니다. 새 **항목 추가** 대화 상자에서 **시각적 C#** > **확장성으로** 이동하여 **사용자 지정 명령을 선택합니다.** 창 아래쪽의 **이름** 필드에서 명령 파일 이름을 *GetServiceCommand.cs.* 사용자 지정 명령을 만드는 방법에 대 한 자세한 내용은 [메뉴 명령을 사용하여 확장](../extensibility/creating-an-extension-with-a-menu-command.md) 만들기

3. *GetServiceCommand.cs* `MenuItemCommand` 메서드 본문을 제거하고 다음 코드를 추가합니다.

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    이 코드는 SVsActivityLog 서비스를 받고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 활동 로그에 쓰는 데 사용할 수 있는 인터페이스로 캐스팅합니다. 예를 들어 사용 [방법: 활동 로그를 사용합니다.](../extensibility/how-to-use-the-activity-log.md)

4. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타납니다.

5. 실험 인스턴스의 **도구** 메뉴에서 **GetServiceCommand 호출** 단추를 찾습니다. 이 단추를 클릭하면 **활동 로그 서비스 발견이라는 메시지 상자가 표시됩니다.**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>도구 창 또는 제어 컨테이너에서 서비스 받기

경우에 따라 사이트되지 않은 도구 창 또는 제어 컨테이너에서 서비스를 받아야 하거나 원하는 서비스에 대해 모르는 서비스 공급자와 함께 사이트를 지정해야 할 수도 있습니다. 예를 들어 컨트롤 내에서 활동 로그에 쓸 수 있습니다.

정적 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 메서드는 VSPackage에서 파생된 모든 것이 처음 사이트에 사이트에 지정될 <xref:Microsoft.VisualStudio.Shell.Package> 때 초기화되는 캐시된 서비스 공급자에 의존합니다.

VSPackage 생성자는 VSPackage가 사이트를 지정하기 전에 호출되므로 VSPackage 생성자 내에서 전역 서비스를 사용할 수 없습니다. 해결 방법: 해결 방법은 [서비스 문제 해결을 참조하세요.](../extensibility/how-to-troubleshoot-services.md)

다음은 도구 창 또는 기타 VSPackage가 아닌 요소에서 서비스를 받는 방법의 예입니다.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>DTE 개체에서 서비스 받기

개체에서 <xref:EnvDTE.DTEClass> 서비스를 받을 수도 있습니다. 그러나 VSPackage에서 서비스로 또는 정적 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 메서드를 호출 하여 DTE 개체를 얻어야 합니다.

DTE 개체는 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>을 사용하여 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>서비스를 쿼리하는 데 사용할 수 있는 을 구현합니다.

DTE 개체에서 서비스를 받는 방법은 다음과 같습니다.

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

## <a name="see-also"></a>참조

- [방법: 서비스 제공](../extensibility/how-to-provide-a-service.md)
- [서비스 사용 및 제공](../extensibility/using-and-providing-services.md)
- [서비스 필수 요소](../extensibility/internals/service-essentials.md)

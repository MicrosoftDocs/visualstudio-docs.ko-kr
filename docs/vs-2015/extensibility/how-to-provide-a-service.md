---
title: '방법: 서비스 제공 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 565a8a91797c826b6419dc5a8488d7d3baf9cddc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841715"
---
# <a name="how-to-provide-a-service"></a>방법: 서비스 제공
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage는 다른 Vspackage에서 사용할 수 있는 서비스를 제공할 수 있습니다. 서비스를 제공 하려면 VSPackage이 서비스를 Visual Studio에 등록 하 고 서비스를 추가 해야 합니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Package>클래스는 및를 둘 다 구현 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> <xref:System.ComponentModel.Design.IServiceContainer> 합니다. <xref:System.ComponentModel.Design.IServiceContainer> 요청 시 서비스를 제공 하는 콜백 메서드를 포함 합니다.  
  
 서비스에 대 한 자세한 내용은 [Service Essentials](../extensibility/internals/service-essentials.md) 를 참조 하세요.  
  
> [!NOTE]
> VSPackage가 언로드되는 경우 Visual Studio는 VSPackage가 제공 하는 서비스에 대 한 모든 요청이 배달 될 때까지 대기 합니다. 이러한 서비스에 대 한 새 요청은 허용 되지 않습니다. <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A>언로드할 때 서비스를 해지 하려면 메서드를 명시적으로 호출 하면 안 됩니다.  
  
#### <a name="implementing-a-service"></a>서비스 구현  
  
1. VSIX 프로젝트를 만듭니다 (**File/New/project/Visual c #/확장성/Vsix 프로젝트**).  
  
2. 프로젝트에 VSPackage를 추가 합니다. **솔루션 탐색기** 에서 프로젝트 노드를 선택 하 고 **추가/새 항목/Visual c # 항목/확장성/visual Studio 패키지**를 클릭 합니다.  
  
3. 서비스를 구현 하려면 다음 세 가지 유형을 만들어야 합니다.  
  
   - 서비스를 설명 하는 인터페이스입니다. 이러한 인터페이스 중 상당수는 비어 있습니다. 즉, 메서드가 없습니다.  
  
   - 서비스 인터페이스를 설명 하는 인터페이스입니다. 이 인터페이스는 구현 될 메서드를 포함 합니다.  
  
   - 서비스와 서비스 인터페이스를 둘 다 구현 하는 클래스입니다.  
  
     다음 예제에서는 세 가지 형식의 매우 기본적인 구현을 보여 줍니다. 서비스 클래스의 생성자는 서비스 공급자를 설정 해야 합니다.  
  
   ```csharp  
   public class MyService : SMyService, IMyService  
   {  
       private Microsoft.VisualStudio.OLE.Interop.IServiceProvider serviceProvider;  
       private string myString;  
       public MyService(Microsoft.VisualStudio.OLE.Interop.IServiceProvider sp)  
       {  
           Trace.WriteLine(  
                  "Constructing a new instance of MyService");  
           serviceProvider = sp;  
       }  
       public void Hello()  
       {  
           myString = "hello";  
       }  
       public string Goodbye()  
       {  
          return "goodbye";  
       }  
   }  
   public interface SMyService  
   {  
   }  
   public interface IMyService  
   {  
       void Hello();  
       string Goodbye();  
   }  
  
   ```  
  
### <a name="registering-a-service"></a>서비스 등록  
  
1. 서비스를 등록 하려면 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 서비스를 제공 하는 VSPackage에를 추가 합니다. 다음은 예제입니다.  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     이 특성 `SMyService` 은 Visual Studio에 등록 됩니다.  
  
    > [!NOTE]
    > 다른 서비스를 같은 이름으로 대체 하는 서비스를 등록 하려면를 사용 <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> 합니다. 서비스의 재정의는 하나만 허용 됩니다.  
  
### <a name="adding-a-service"></a>서비스 추가  
  
1. 1.  VSPackage 이니셜라이저에서 서비스를 추가 하 고 콜백 메서드를 추가 하 여 서비스를 만듭니다. 이 메서드에 대 한 변경 내용은 다음과 같습니다 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2. 서비스를 만들고 반환 하는 콜백 메서드를 구현 하거나 만들 수 없는 경우 null을 구현 합니다.  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    > Visual Studio는 서비스를 제공 하는 요청을 거부할 수 있습니다. 다른 VSPackage 이미 서비스를 제공 하는 경우이를 수행 합니다.  
  
3. 이제 서비스를 가져오고 해당 메서드를 사용할 수 있습니다. 이는 이니셜라이저에 표시 되지만 서비스를 사용 하려는 모든 위치에서 서비스를 가져올 수 있습니다.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
  
        MyService myService = (MyService) this.GetService(typeof(SMyService));  
        myService.Hello();  
        string helloString = myService.myString;  
  
        base.Initialize();  
    }  
    ```  
  
     값은 `helloString` "Hello" 여야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [방법: 서비스 가져오기](../extensibility/how-to-get-a-service.md)   
 [서비스 사용 및 제공](../extensibility/using-and-providing-services.md)   
 [서비스 필수 항목](../extensibility/internals/service-essentials.md)

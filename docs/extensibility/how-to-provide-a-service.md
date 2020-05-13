---
title: '방법: 서비스 제공 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60cae5e8048a0234114e1f9e7d97728e26ee40f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710781"
---
# <a name="how-to-provide-a-service"></a>방법: 서비스 제공
VSPackage는 다른 VSPackage에서 사용할 수 있는 서비스를 제공할 수 있습니다. 서비스를 제공하려면 VSPackage가 Visual Studio에 서비스를 등록하고 서비스를 추가해야 합니다.

 클래스는 <xref:Microsoft.VisualStudio.Shell.Package> 모두 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 및 <xref:System.ComponentModel.Design.IServiceContainer>을 구현합니다. <xref:System.ComponentModel.Design.IServiceContainer>에는 주문형 서비스를 제공하는 콜백 메서드가 포함되어 있습니다.

 서비스에 대한 자세한 내용은 [서비스 필수 정보를](../extensibility/internals/service-essentials.md) 참조하십시오.

> [!NOTE]
> VSPackage가 언로드될 예정이면 Visual Studio는 VSPackage가 제공하는 서비스에 대한 모든 요청이 배달될 때까지 기다립니다. 이러한 서비스에 대한 새 요청은 허용되지 않습니다. 언로드 할 때 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> 서비스를 해지하는 메서드를 명시적으로 호출해서는 안됩니다.

## <a name="implement-a-service"></a>서비스 구현

1. VSIX 프로젝트 >  > **Project** >  > **만들기(파일 새**프로젝트**Visual C#** > **확장성****VSIX 프로젝트).****File**

2. 프로젝트에 VS패키지를 추가합니다. **솔루션 탐색기에서** 프로젝트 노드를 선택하고**새 항목** > Visual**C# 항목** > **확장성** > **Visual Studio 패키지** **추가를** > 클릭합니다.

3. 서비스를 구현하려면 다음 세 가지 유형을 만들어야 합니다.

   - 서비스를 설명하는 인터페이스입니다. 이러한 인터페이스의 대부분은 비어 있습니다, 즉, 그들은 아무 메서드가 없습니다.

   - 서비스 인터페이스를 설명하는 인터페이스입니다. 이 인터페이스에는 구현할 메서드가 포함됩니다.

   - 서비스와 서비스 인터페이스를 모두 구현하는 클래스입니다.

     다음 예제에서는 세 가지 형식의 기본 구현을 보여 주다. 서비스 클래스의 생성자는 서비스 공급자를 설정해야 합니다.

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

### <a name="register-a-service"></a>서비스 등록

1. 서비스를 등록하려면 서비스를 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 제공하는 VSPackage에 추가합니다. 다음은 예제입니다.

    ```csharp
    [ProvideService(typeof(SMyService))]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [Guid(VSPackage1.PackageGuidString)]
    public sealed class VSPackage1 : Package
    {. . . }
    ```

     이 특성은 `SMyService` Visual Studio에 등록됩니다.

    > [!NOTE]
    > 다른 서비스를 동일한 이름으로 대체하는 서비스를 등록하려면 을 <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>사용합니다. 서비스의 재정의는 하나만 허용됩니다.

### <a name="add-a-service"></a>서비스 추가

1. VSPackage 초기화자에서 서비스를 추가하고 콜백 메서드를 추가하여 서비스를 만듭니다. <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 메서드를 변경한 내용은 다음과 같습니다.

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);
    . . .
    }
    ```

2. 서비스를 만들고 반환해야 하는 콜백 메서드를 구현하거나 만들 수 없는 경우 null을 구현합니다.

    ```csharp
    private object CreateService(IServiceContainer container, Type serviceType)
    {
        if (typeof(SMyService) == serviceType)
            return new MyService(this);
        return null;
    }
    ```

    > [!NOTE]
    > Visual Studio는 서비스 제공 요청을 거부할 수 있습니다. 다른 VSPackage가 이미 서비스를 제공하는 경우 그렇게 합니다.

3. 이제 서비스를 받고 해당 메서드를 사용할 수 있습니다. 아래 예제는 초기화기에서 서비스를 사용하는 방법을 보여 주지만 서비스를 사용하려는 모든 곳에서 서비스를 받을 수 있습니다.

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);

        MyService myService = (MyService) this.GetService(typeof(SMyService));
        myService.Hello();
        string helloString = myService.Goodbye();

        base.Initialize();
    }
    ```

     의 `helloString` 값은 "안녕하세요"여야합니다.

## <a name="see-also"></a>참조
- [방법: 서비스 받기](../extensibility/how-to-get-a-service.md)
- [서비스 사용 및 제공](../extensibility/using-and-providing-services.md)
- [서비스 필수 요소](../extensibility/internals/service-essentials.md)

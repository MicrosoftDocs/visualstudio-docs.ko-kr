---
title: '방법: 비동기 비주얼 스튜디오 서비스 제공 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65362e465beec5465903083beca069104a48166b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710762"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>방법: 비동기 Visual Studio 서비스 제공
UI 스레드를 차단하지 않고 서비스를 가져오려면 비동기 서비스를 만들고 백그라운드 스레드에서 패키지를 로드해야 합니다. 이를 위해 <xref:Microsoft.VisualStudio.Shell.AsyncPackage> <xref:Microsoft.VisualStudio.Shell.Package>을 대신 사용하고 비동기 패키지의 특수 비동기 메서드를 사용하여 서비스를 추가할 수 있습니다.

 동기 Visual Studio 서비스 제공에 대한 자세한 내용은 [서비스 제공 방법:을](../extensibility/how-to-provide-a-service.md)참조하십시오.

## <a name="implement-an-asynchronous-service"></a>비동기 서비스 구현

1. VSIX 프로젝트 >  > **Project** >  > **만들기(파일 새**프로젝트**Visual C#** > **확장성****VSIX 프로젝트).****File** 프로젝트 **TestAsync**의 이름을 지정합니다.

2. 프로젝트에 VS패키지를 추가합니다. **솔루션 탐색기에서** 프로젝트 노드를 선택하고**새 항목** > Visual**C# 항목** > **확장성** > **Visual Studio 패키지** **추가를** > 클릭합니다. 이 파일의 이름을 *TestAsyncPackage.cs.*

3. *TestAsyncPackage.cs*패키지를 `AsyncPackage` 다음이 아닌 `Package`상속하도록 변경합니다.

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. 서비스를 구현하려면 다음 세 가지 유형을 만들어야 합니다.

    - 서비스를 식별하는 인터페이스입니다. 이러한 인터페이스의 대부분은 비어 있습니다.

    - 서비스 인터페이스를 설명하는 인터페이스입니다. 이 인터페이스에는 구현할 메서드가 포함됩니다.

    - 서비스와 서비스 인터페이스를 모두 구현하는 클래스입니다.

5. 다음 예제에서는 세 가지 형식의 매우 기본적인 구현을 보여 주다. 서비스 클래스의 생성자는 서비스 공급자를 설정해야 합니다. 이 예제에서는 패키지 코드 파일에 서비스를 추가합니다.

6. 패키지 파일에 지시문을 사용하여 다음을 추가합니다.

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. 다음은 비동기 서비스 구현입니다. 생성자의 동기 서비스 공급자가 아니라 비동기 서비스 공급자를 설정해야 합니다.

    ```csharp
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private IAsyncServiceProvider asyncServiceProvider;

        public TextWriterService(IAsyncServiceProvider provider)
        {
            // constructor should only be used for simple initialization
            // any usage of Visual Studio service, expensive background operations should happen in the
            // asynchronous InitializeAsync method for best performance
            asyncServiceProvider = provider;
        }

        public async Task InitializeAsync(CancellationToken cancellationToken)
        {
            await TaskScheduler.Default;
            // do background operations that involve IO or other async methods

            await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
            // query Visual Studio services on main thread unless they are documented as free threaded explicitly.
            // The reason for this is the final cast to service interface (such as IVsShell) may involve COM operations to add/release references.

            IVsShell vsShell = this.asyncServiceProvider.GetServiceAsync(typeof(SVsShell)) as IVsShell;
            // use Visual Studio services to continue initialization
        }

        public async Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
    }

    public interface STextWriterService
    {
    }

    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
    }
    ```

## <a name="register-a-service"></a>서비스 등록
 서비스를 등록하려면 서비스를 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 제공하는 패키지에 를 추가합니다. 동기 서비스를 등록하는 경우와 달리 패키지와 서비스가 비동기 로드를 모두 지원하는지 확인해야 합니다.

- 패키지등록특성에 대한 자세한 내용은 등록 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 및 등록 취소 [VSPackage를](../extensibility/registering-and-unregistering-vspackages.md)참조하여 패키지를 비동기적으로 초기화할 수 있도록 허용 배경 로드 = **true** 필드를 추가해야 합니다.

- 서비스 인스턴스를 비동기적으로 초기화할 수 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 있도록 **IsAsyncQueryable = true** 필드를 추가해야 합니다.

  다음은 비동기 서비스 `AsyncPackage` 등록이 있는 의 예입니다.

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>서비스 추가

1. *TestAsyncPackage.cs*메서드를 `Initialize()` 제거하고 메서드를 `InitializeAsync()` 재정의합니다. 서비스를 추가하고 콜백 메서드를 추가하여 서비스를 만듭니다. 다음은 서비스를 추가하는 비동기 초기화자의 예입니다.

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```
    이 패키지 외부에서 이 서비스를 표시하려면 승격 플래그 값을 *true로* 설정합니다.`this.AddService(typeof(STextWriterService), CreateTextWriterService, true);`

2. *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll에*대한 참조를 추가합니다.

3. 콜백 메서드를 만들고 서비스를 반환 하는 비동기 메서드로 구현 합니다.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>서비스 사용
 이제 서비스를 받고 해당 메서드를 사용할 수 있습니다.

1. 초기화에 이 것을 표시하지만 서비스를 사용하려는 모든 곳에서 서비스를 받을 수 있습니다.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
    }

    ```

     컴퓨터에서 의미가 있는 `userpath` 파일 이름과 경로로 변경하는 것을 잊지 마십시오!

2. 코드를 빌드하고 실행합니다. Visual Studio의 실험 인스턴스가 나타나면 솔루션을 엽니다. 이로 인해 `AsyncPackage` 자동 로드가 발생합니다. 초기화가 실행되면 지정한 위치에서 파일을 찾아야 합니다.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>명령 처리기에서 비동기 서비스 사용
 다음은 메뉴 명령에서 비동기 서비스를 사용하는 방법의 예입니다. 여기에 표시된 절차를 사용하여 다른 비동기 메서드에서 서비스를 사용할 수 있습니다.

1. 프로젝트에 메뉴 명령을 추가합니다. (솔루션 **탐색기에서**프로젝트 노드를 선택하고 마우스 오른쪽 단추로 클릭하고 새 > **항목** > **확장성** > 사용자 지정 명령 **추가를**선택합니다.)**Custom Command** 명령 파일의 이름을 *TestAsyncCommand.cs.*

2. 사용자 지정 명령 템플릿은 `Initialize()` 명령을 초기화하기 위해 *TestAsyncPackage.cs* 파일에 메서드를 다시 추가합니다. 메서드에서 `Initialize()` 명령을 초기화하는 줄을 복사합니다. 다음과 같이 표시되어야 합니다.

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     이 줄을 `InitializeAsync()` *AsyncPackageForService.cs* 파일의 메서드로 이동합니다. 비동기 초기화이므로 을 사용하여 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>명령을 초기화하기 전에 기본 스레드로 전환해야 합니다. 이제 다음과 같이 표시됩니다.

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");

        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
        TestAsyncCommand.Initialize(this);
    }

    ```

3. 메서드를 `Initialize()` 삭제합니다.

4. *TestAsyncCommand.cs* 파일에서 메서드를 `MenuItemCallback()` 찾습니다. 메서드의 본문을 삭제합니다.

5. using 지시문 추가:

    ```csharp
    using System.IO;
    ```

6. 서비스를 받고 해당 메서드를 `UseTextWriterAsync()`사용하는 비동기 메서드를 추가합니다.

    ```csharp
    private async System.Threading.Tasks.Task UseTextWriterAsync()
    {
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))
              as ITextWriterService;

        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
       }

    ```

7. 메서드에서 이 `MenuItemCallback()` 메서드를 호출합니다.

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. 솔루션을 빌드하고 디버깅을 시작합니다. Visual Studio의 실험 인스턴스가 나타나면 **도구** 메뉴로 이동하여 **TestAsyncCommand 호출** 메뉴 항목을 찾습니다. 클릭하면 TextWriterService가 지정한 파일에 기록됩니다. (명령을 호출하면 패키지가 로드되기 때문에 솔루션을 열 필요가 없습니다.)

## <a name="see-also"></a>참조
- [서비스 사용 및 제공](../extensibility/using-and-providing-services.md)

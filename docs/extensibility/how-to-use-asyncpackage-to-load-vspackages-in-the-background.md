---
title: '방법: 비동기 패키지를 사용하여 백그라운드에서 VSPackage로드 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: 77690a1947f82f97c4aa12809a80ea61335d216d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710626"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>방법: 비동기 패키지를 사용하여 백그라운드에서 VSPackage로드
VS 패키지를 로드하고 초기화하면 디스크 I/O가 발생할 수 있습니다. UI 스레드에서 이러한 I/O가 발생하면 응답성 문제가 발생할 수 있습니다. 이 문제를 해결하기 위해 Visual Studio <xref:Microsoft.VisualStudio.Shell.AsyncPackage> 2015는 백그라운드 스레드에서 패키지를 로드할 수 있는 클래스를 도입했습니다.

## <a name="create-an-asyncpackage"></a>비동기 패키지 만들기
 VSIX > **Visual Studio Package** > **New Item** >  >  > **Project** >  > **프로젝트(파일 새**프로젝트**File****Visual C#****확장성** > **VSIX 프로젝트)를**만들고 프로젝트에 VSPackage를 추가하여 시작할 수 있습니다(프로젝트를 마우스 오른쪽 버튼으로 클릭하고 새 항목**C# 항목** > **확장성**시각적 스튜디오 패키지 **추가).** 그런 다음 서비스를 만들고 해당 서비스를 패키지에 추가할 수 있습니다.

1. 에서 <xref:Microsoft.VisualStudio.Shell.AsyncPackage>패키지를 파생합니다.

2. 쿼리로 인해 패키지가 로드될 수 있는 서비스를 제공하는 경우:

    패키지가 백그라운드 로드에 안전하다는 것을 Visual Studio에 나타내고 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 이 동작을 선택하려면 Attribute 생성자에서 **AllowBackgroundLoading** 속성을 true로 설정해야 합니다.

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    Visual Studio에 백그라운드 스레드에서 서비스를 인스턴스화하는 것이 안전하다는 것을 나타내려면 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 생성자에서 속성을 true로 설정해야 합니다.

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. UI 컨텍스트를 통해 로드 하는 경우 다음 지정 해야 **PackageAutoLoadFlags.BackgroundLoad** <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 또는 값 (0x2) 패키지의 자동 로드 항목의 값으로 작성 된 플래그에.

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. 비동기 초기화 작업이 있는 경우 을 재정의해야 <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>합니다. VSIX `Initialize()` 템플릿에서 제공하는 메서드를 제거합니다. `Initialize()` (비동기 **패키지의** 메서드가 봉인됩니다.) 모든 메서드를 사용하여 <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> 패키지에 비동기 서비스를 추가할 수 있습니다.

    참고: 를 `base.InitializeAsync()`호출하려면 소스 코드를 다음으로 변경할 수 있습니다.

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. 비동기 초기화 **코드(InitializeAsync)에서**RPC(원격 프로시저 호출)를 만들지 않도록 주의해야 합니다. 이러한 경우 직접 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 또는 간접적으로 호출할 때 발생할 수 있습니다.  동기화 로드가 필요한 경우 UI 스레드는 을 사용하여 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>차단합니다. 기본 차단 모델은 RPC를 사용하지 않도록 설정합니다. 즉, 비동기 작업에서 RPC를 사용하려고 하면 UI 스레드가 패키지가 로드되기를 기다리는 경우 교착 상태가 됩니다. 일반적인 대안은 **Joinable 작업 팩터리** <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> 또는 RPC를 사용하지 않는 다른 메커니즘과 같은 작업을 사용하여 필요한 경우 코드를 UI 스레드로 마샬링하는 것입니다.  **ThreadHelper.Generic.Invoke를** 사용하거나 일반적으로 UI 스레드에 도착하기 위해 대기하는 호출 스레드를 차단하지 마십시오.

    참고: 메서드에서 **GetService** 또는 **QueryService를** 사용하지 않아야 합니다. `InitializeAsync` 이러한 스레드를 사용해야 하는 경우 먼저 UI 스레드로 전환해야 합니다. 대안은 <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> **AsyncPackage에서** 사용하는 것입니다 (로 <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>캐스팅하여.)

   C#: 비동기 패키지 만들기:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]
public sealed class TestPackage : AsyncPackage
{
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(SMyTestService), CreateService, true);
        return Task.FromResult<object>(null);
    }
}
```

## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>기존 VS패키지를 비동기 패키지로 변환
 대부분의 작업은 새 **AsyncPackage**를 만드는 것과 동일합니다. 위의 1-5단계를 따르십시오. 또한 다음 권장 사항에 유의해야 합니다.

1. 패키지에 있던 `Initialize` 재정의를 제거해야 합니다.

2. 교착 상태 방지: 코드에 숨겨진 RPC가 있을 수 있습니다. 이제 백그라운드 스레드에서 발생합니다. RPC(예: **GetService)를**만드는 경우 (1) 주 스레드로 전환하거나 (2) API의 비동기 버전(예: **GetServiceAsync)을**사용해야 합니다.

3. 스레드 간을 너무 자주 전환하지 마십시오. 로드 시간을 줄이기 위해 백그라운드 스레드에서 발생할 수 있는 작업을 지역화해 보십시오.

## <a name="querying-services-from-asyncpackage"></a>애싱크패키지에서 서비스 쿼리
 **AsyncPackage** 호출자에 따라 비동기적으로 로드되거나 로드되지 않을 수 있습니다. 예를 들어

- 호출자가 **GetService** 또는 **QueryService(모두** 동기 API) 또는

- 호출자가 **IVsShell::LoadPackage(또는** **IVsShell5::LoadPackageWithContext)라고**하는 경우 또는

- 로드는 UI 컨텍스트에 의해 트리거되지만 UI 컨텍스트 메커니즘을 지정하지 않아 비동기적으로 로드할 수 있습니다.

  그러면 패키지가 동기적으로 로드됩니다.

  패키지에는 UI 스레드가 해당 작업의 완료에 대해 차단되지만 패키지에 는 UI 스레드에서 작업을 수행할 수 있는 기회가 여전히 있습니다. 호출자는 **IAsyncServiceProvider를** 사용하여 서비스를 비동기적으로 쿼리하는 경우 결과 작업 개체에서 즉시 차단하지 않는다고 가정하여 로드 및 초기화가 비동기적으로 수행됩니다.

  C#: 서비스를 비동기적으로 쿼리하는 방법:

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```

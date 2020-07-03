---
title: '방법: AsyncPackage를 사용 하 여 백그라운드에서 Vspackage 로드 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: 7727d53c84ab876fe6616c8ec5d438033216481e
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905596"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>방법: AsyncPackage를 사용 하 여 백그라운드에서 Vspackage 로드
VS 패키지를 로드 하 고 초기화 하면 디스크 i/o가 발생할 수 있습니다. 이러한 i/o가 UI 스레드에서 발생 하면 응답성 문제가 발생할 수 있습니다. 이를 해결 하기 위해 Visual Studio 2015에서는 <xref:Microsoft.VisualStudio.Shell.AsyncPackage> 백그라운드 스레드에서 패키지를 로드할 수 있도록 하는 클래스를 도입 했습니다.

## <a name="create-an-asyncpackage"></a>AsyncPackage 만들기
 먼저 VSIX 프로젝트를 만들고 (**파일**  >  **새로 만들기**  >  **프로젝트**  >  **Visual c #**  >  **확장성**  >  **VSIX 프로젝트**) VSPackage를 프로젝트에 추가할 수 있습니다 (프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **Add**  >  **새 항목**추가  >  **c # 항목**  >  **확장성**  >  **Visual Studio 패키지**). 그런 다음 서비스를 만들어 패키지에 추가할 수 있습니다.

1. 에서 패키지를 파생 시킵니다 <xref:Microsoft.VisualStudio.Shell.AsyncPackage> .

2. 쿼리가 패키지를 로드 하는 데 사용할 수 있는 서비스를 제공 하는 경우:

    Visual Studio에서 패키지가 백그라운드 로드를 위해 안전 하 고이 동작을 옵트인 (opt in) 할 수 있도록 하려면 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 특성 생성자에서 **AllowsBackgroundLoading** 속성을 true로 설정 해야 합니다.

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    Visual Studio에서 백그라운드 스레드에서 서비스를 인스턴스화하는 것이 안전 하다는 것을 나타내려면 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> 생성자에서 속성을 true로 설정 해야 합니다 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> .

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. UI 컨텍스트를 통해 로드 하는 경우 패키지의 자동 로드 항목 값으로 작성 된 플래그에 또는 값 (0x2)에 대해 **Packageautoloadflags** 를 지정 해야 합니다. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. 비동기 초기화 작업을 수행 하려면를 재정의 해야 <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A> 합니다. `Initialize()`VSIX 템플릿에서 제공 하는 메서드를 제거 합니다. ( `Initialize()` **Asyncpackage** 의 메서드는 봉인 되어 있습니다.) 메서드 중 하나 <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> 를 사용 하 여 패키지에 비동기 서비스를 추가할 수 있습니다.

    참고:를 호출 하기 위해 `base.InitializeAsync()` 소스 코드를 다음과 같이 변경할 수 있습니다.

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. 비동기 초기화 코드 ( **InitializeAsync**)에서 Rpc (원격 프로시저 호출)를 수행 하지 않도록 주의 해야 합니다. 이러한 오류는 직접 또는 간접적으로 호출 하는 경우 발생할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> .  동기화 로드가 필요한 경우 UI 스레드는를 사용 하 여 차단 됩니다 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> . 기본 차단 모델은 Rpc를 사용 하지 않도록 설정 합니다. 즉, 비동기 작업에서 RPC를 사용 하려는 경우 UI 스레드가 자체 패키지 로드를 대기 하는 경우 교착 상태가 발생 합니다. 일반적인 대안은 **조인 가능 작업 팩터리** <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> 또는 RPC를 사용 하지 않는 다른 메커니즘과 같은 항목을 사용 하 여 필요한 경우 코드를 UI 스레드로 마샬링하는 것입니다.  Threadhelper를 사용 하지 마십시오. **제네릭. Invoke** 를 사용 하거나 일반적으로 UI 스레드로 가져오기 위해 대기 중인 호출 스레드를 차단 합니다.

    참고: 메서드에서 **GetService** 또는 **QueryService** 를 사용 하지 않도록 해야 합니다 `InitializeAsync` . 이를 사용 해야 하는 경우 먼저 UI 스레드로 전환 해야 합니다. 대신 <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> 을로 캐스팅 하 여 **asyncpackage** 에서를 사용 하는 것이 좋습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider> .

   C #: AsyncPackage를 만듭니다.

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

## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>기존 VSPackage을 AsyncPackage로 변환
 대부분의 작업은 새 **Asyncpackage**를 만드는 것과 동일 합니다. 위의 1 ~ 5 단계를 수행 합니다. 또한 다음과 같은 권장 사항을 추가로 주의 해야 합니다.

1. `Initialize`패키지에 있던 재정의는 제거 해야 합니다.

2. 교착 상태 방지: 코드에 숨겨진 Rpc가 있을 수 있습니다. 이제 백그라운드 스레드에서 발생 합니다. RPC를 만드는 경우 (예: **GetService**), (1) 주 스레드로 전환 하거나 (2) 비동기 버전의 API (예: **GetServiceAsync**)를 사용 해야 합니다.

3. 스레드를 너무 자주 전환 하지 마십시오. 로드 시간을 줄이기 위해 백그라운드 스레드에서 발생할 수 있는 작업을 지역화 하려고 합니다.

## <a name="querying-services-from-asyncpackage"></a>AsyncPackage에서 서비스 쿼리
 **Asyncpackage** 는 호출자에 따라 비동기적으로 로드 될 수도 있고 그렇지 않을 수도 있습니다. 예를 들어

- 호출자가 **GetService** 또는 **QueryService** (동기 api)를 호출한 경우

- 호출자가 **Ivsshell:: LoadPackage** (또는 **IVsShell5:: LoadPackageWithContext**)를 호출한 경우

- 부하는 UI 컨텍스트에 의해 트리거되고 UI 컨텍스트 메커니즘이 비동기적으로 로드 될 수 있도록 지정 하지 않았습니다.

  그런 다음 패키지가 동기적으로 로드 됩니다.

  해당 작업의 완료에 대 한 UI 스레드가 차단 되는 경우에도 패키지에는 비동기 초기화 단계에서 UI 스레드 작업을 수행할 수 있는 기회가 있습니다. 호출자가 **IAsyncServiceProvider** 를 사용 하 여 서비스에 대 한 비동기 쿼리를 수행 하는 경우 생성 된 작업 개체를 즉시 차단 하지 않는다고 가정 하 고 로드 및 초기화가 비동기적으로 수행 됩니다.

  C #: 비동기적으로 서비스를 쿼리 하는 방법:

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```

---
title: '방법: 관리 코드 | 여러 스레드 관리 Microsoft Docs'
description: 관리되는 VSPackage 확장이 비동기 메서드를 호출하거나 Visual Studio UI 스레드에서 작업을 수행할 경우 코드에서 여러 스레드를 관리하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 39319b748dd41c6936e7b70e20243202452fae67
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903088"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>방법: 관리 코드에서 여러 스레드 관리
비동기 메서드를 호출하거나 Visual Studio UI 스레드 이외의 스레드에서 실행되는 작업이 있는 관리되는 VSPackage 확장이 있는 경우 아래에 제공된 지침을 따라야 합니다. 다른 스레드에서 작업이 완료되기를 기다릴 필요가 없으므로 UI 스레드의 응답성을 유지할 수 있습니다. 스택 공간을 차지 하는 추가 스레드가 없기 때문에 코드를 보다 효율적으로 만들 수 있으며 교착 상태와 응답하지 않는 코드를 방지하므로 보다 안정적이고 쉽게 디버그할 수 있습니다.

 일반적으로 UI 스레드에서 다른 스레드로 전환하거나 그 반대로 전환할 수 있습니다. 메서드가 반환되면 현재 스레드는 원래 호출된 스레드입니다.

> [!IMPORTANT]
> 다음 지침에서는 <xref:Microsoft.VisualStudio.Threading> 네임스페이스, 특히 클래스의 API를 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> 사용합니다. 이 네임스페이스의 API는 의 새로운 [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] API입니다. 의 인스턴스를 속성 에서 얻을 수 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> <xref:Microsoft.VisualStudio.Shell.ThreadHelper> `ThreadHelper.JoinableTaskFactory` 있습니다.

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>UI 스레드에서 백그라운드 스레드로 전환

1. UI 스레드에 있고 백그라운드 스레드에서 비동기 작업을 수행하려면 를 `Task.Run()` 사용합니다.

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. UI 스레드에 있고 백그라운드 스레드에서 작업을 수행하는 동안 동기적으로 차단하려는 경우 내부의 속성을 사용합니다. <xref:System.Threading.Tasks.TaskScheduler> `TaskScheduler.Default` <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>백그라운드 스레드에서 UI 스레드로 전환

1. 백그라운드 스레드에 있고 UI 스레드에서 작업을 수행하려면 를 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> 사용합니다.

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     메서드를 사용하여 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> UI 스레드로 전환할 수 있습니다. 이 메서드는 현재 비동기 메서드의 연속으로 UI 스레드에 메시지를 게시하고, 스레딩 프레임워크의 나머지 부분과 통신하여 올바른 우선 순위를 설정하고 교착 상태를 방지합니다.

     백그라운드 스레드 메서드가 비동기 메서드가 아니고 비동기로 만들 수 없는 경우에도 다음 예제와 같이 로 `await` 작업을 래핑하여 구문을 사용하여 UI 스레드로 전환할 수 있습니다. <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```

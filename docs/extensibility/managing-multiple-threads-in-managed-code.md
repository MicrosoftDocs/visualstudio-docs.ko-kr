---
title: '방법: 관리 코드에서 여러 스레드 관리 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceaa0af4f57fe374cf9cf4b2dd8b4f40af74a852
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702777"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>방법: 관리 코드에서 여러 스레드 관리
비동기 메서드를 호출하거나 Visual Studio UI 스레드 가 아닌 스레드에서 실행되는 작업이 있는 관리되는 VSPackage 확장이 있는 경우 아래 지침을 따라야 합니다. 다른 스레드에서 작업이 완료될 때까지 기다릴 필요가 없으므로 UI 스레드를 응답 상태로 유지할 수 있습니다. 스택 공간을 차지하는 추가 스레드가 없기 때문에 코드를 보다 효율적으로 만들 수 있으며 교착 상태와 중단을 피하기 때문에 보다 안정적이고 쉽게 디버깅할 수 있습니다.

 일반적으로 UI 스레드에서 다른 스레드로 전환하거나 그 반대로 전환할 수 있습니다. 메서드가 반환되면 현재 스레드는 원래 호출된 스레드입니다.

> [!IMPORTANT]
> 다음 지침은 <xref:Microsoft.VisualStudio.Threading> 네임스페이스, 특히 클래스의 API를 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> 사용합니다. 이 네임스페이스의 API는 [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]에 새로 들어있습니다. 속성에서 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> <xref:Microsoft.VisualStudio.Shell.ThreadHelper> `ThreadHelper.JoinableTaskFactory`a의 인스턴스를 얻을 수 있습니다.

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>UI 스레드에서 백그라운드 스레드로 전환

1. UI 스레드에 있고 백그라운드 스레드에서 비동기 작업을 수행하려는 경우 `Task.Run()`다음을 사용합니다.

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. UI 스레드에 있고 백그라운드 스레드에서 작업을 수행하는 동안 동기적으로 차단하려는 경우 다음 <xref:System.Threading.Tasks.TaskScheduler> `TaskScheduler.Default` 안에 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>속성을 사용합니다.

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

1. 백그라운드 스레드에 있고 UI 스레드에서 작업을 수행하려는 경우 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>다음을 사용합니다.

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     이 메서드를 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> 사용하여 UI 스레드로 전환할 수 있습니다. 이 메서드는 현재 비동기 메서드의 연속과 함께 UI 스레드에 메시지를 게시 하 고 올바른 우선 순위를 설정 하 고 교착 상태를 방지 하기 위해 스레딩 프레임 워크의 나머지와 통신.

     백그라운드 스레드 메서드가 비동기가 아니고 비동기로 만들 수 없는 경우에도 `await` 구문을 사용하여 다음 예제와 같이 작업을 다음과 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>같이 래핑하여 UI 스레드로 전환할 수 있습니다.

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
